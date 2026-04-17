---
description: >-
  Skills let you extend Intelligence Nodes with custom context or custom code
  that runs when the AI decides to use it.
icon: hammer
---

# Skills

{% hint style="success" %}
**Want help building your first Skill?** We'd love to talk. Just [book a training](https://daisychain.app/training) with our team. Skills are available with any [Daisychain subscription](https://www.daisychain.app/pricing).
{% endhint %}

## What is a Skill?

A **Skill** is a custom tool you can attach to an [Intelligence Node](flows.md#intelligence-node-ai-powered). When the AI decides the Skill is relevant to the conversation, it "calls" the Skill and incorporates the result into its reply.

Skills come in two flavors:

* **Content Skills** return a block of markdown to the AI — think of these as reference material the AI can pull in on demand.
* **Code Skills** run a short piece of TypeScript that can call an external API, transform data, and return a structured result to the AI.

You add Skills to a Flow the same way you add built-in tools: open the Intelligence Node, type `@` in the Instructions box, and pick your Skill from the list.

## When to use a Skill

Use a **Content Skill** when the AI needs access to a body of information that is too long or too nuanced to put directly in the Intelligence Node instructions — for example, a position paper, a list of FAQs, or a set of talking points. Keeping this content in a Skill lets the AI pull it in only when needed, which keeps prompts focused and makes the content reusable across Flows.

Use a **Code Skill** when the AI needs to do something dynamic — look up data in an external service, find nearby events for a supporter, check a supporter's donation history, or any other operation that can't be answered from static text.

## Creating a Skill

1. **Naviate to the Flows section of Daisychain** and click the "Customize" link in the top-right. Then, click "Skills."
2. **Click "New Skill"** and give it a name. The name becomes the Skill's tool name (for example, "Healthcare Talking Points" → `skill_healthcare_talking_points`).
3. **Write a description.** The description is shown to the AI, so write it for the AI, not for humans. For example: "Returns the campaign's current talking points about healthcare policy."
4. **Fill in the content or code** depending on the Skill type. A Skill can be content-only, code-only, or both — if both are present, the AI sees the code; the markdown content is available as documentation.
5. **Save.** Then go to any Intelligence Node and add your Skill as a tool.

## Content Skills

A Content Skill is just a markdown document. When the AI calls the Skill, the full content is returned as the tool result and the AI uses it to inform its reply.

{% hint style="info" %}
**Example: "Talking Points About Healthcare"**

**Description:** Returns the campaign's current talking points on healthcare policy. Use this when the supporter asks about the candidate's healthcare stance or raises healthcare concerns.

**Content:**

```markdown
# Healthcare Talking Points

## Our position
We believe healthcare is a human right. Our plan expands Medicare
eligibility to everyone age 50 and up in the first term, and lowers
prescription drug costs by letting Medicare negotiate directly with
manufacturers.

## Key points
- **Lower costs.** Median out-of-pocket costs drop $1,200/year under the plan.
- **More coverage.** An estimated 8 million more people get insurance.
- **Protecting what works.** You keep your current plan if you like it.

## Common questions

**"Does this abolish private insurance?"**
No. Private insurance stays in place. This plan expands Medicare so more
people have an option, it doesn't take existing options away.

**"How is this paid for?"**
The plan is paid for by rolling back the 2017 tax cuts on corporations
and high earners, and by allowing Medicare to negotiate drug prices.

**"What about rural hospitals?"**
The plan includes $25B over ten years dedicated to rural hospital
stabilization.
```
{% endhint %}

In the Intelligence Node instructions, reference the Skill by name so the AI knows when to use it:

> "If the supporter asks about healthcare policy, use the **@Healthcare Talking Points** Skill to ground your reply."

That's it — no code, no schema, no configuration. Content Skills are the fastest way to make long-form context available to a Flow.

## Code Skills

A Code Skill runs a single TypeScript function when the AI calls it. The function receives arguments (chosen by the AI based on an input schema you define), a context object with information about the current person and conversation, and any secrets you've configured.

### The `run` function

Every Code Skill exports a `run` function:

```typescript
export async function run(
  args: SkillArgs,
  context: SkillContext,
  env: Record<string, string>
): Promise<Record<string, unknown>> {
  // your code here
  return { /* anything JSON-serializable */ };
}
```

The returned object is serialized to JSON and handed back to the AI as the tool result. Return any shape you like — just keep it JSON-serializable.

{% hint style="info" %}
**Example: "Dictionary Lookup"**

**Description:** Looks up the definition of a word using the free Dictionary API. Use this when the supporter asks what a word means or when defining a term would help the conversation.

**Input Schema:**

```json
{
  "type": "object",
  "properties": {
    "word": {
      "type": "string",
      "description": "The word to look up, e.g. 'gerrymandering'"
    }
  },
  "required": ["word"]
}
```

**Code (skill.ts):**

```typescript
export async function run(
  args: SkillArgs,
  _context: SkillContext,
  _env: Record<string, string>
): Promise<Record<string, unknown>> {
  const url = `https://api.dictionaryapi.dev/api/v2/entries/en/${encodeURIComponent(args.word)}`;
  const resp = await fetch(url);

  if (resp.status === 404) {
    return { found: false, word: args.word };
  }
  if (!resp.ok) {
    throw new Error(`Lookup failed: ${resp.status} ${resp.statusText}`);
  }

  const entries = await resp.json();
  const first = entries[0];
  const meanings = first.meanings.map((m: { partOfSpeech: string; definitions: { definition: string }[] }) => ({
    partOfSpeech: m.partOfSpeech,
    definition: m.definitions[0]?.definition,
  }));

  return {
    found: true,
    word: first.word,
    phonetic: first.phonetic ?? null,
    meanings,
  };
}
```

When the AI decides to call this Skill, it will pass an argument like `{"word": "gerrymandering"}`, your code fetches the definition, and the AI uses the returned object to compose its reply.
{% endhint %}

### Input Schema — how the AI chooses arguments

The **Input Schema** is a [JSON Schema](https://json-schema.org/) document that describes the arguments your Skill accepts. The AI uses it to decide whether and how to call your Skill, so write it like you're teaching the AI a new API.

A minimal schema looks like this:

```json
{
  "type": "object",
  "properties": {
    "zip_code": {
      "type": "string",
      "description": "The supporter's 5-digit ZIP code"
    },
    "topic": {
      "type": "string",
      "description": "Which issue to return talking points for",
      "enum": ["healthcare", "housing", "education"]
    }
  },
  "required": ["zip_code"]
}
```

Tips for writing schemas that the AI uses well:

* **Describe every property.** The AI reads the `description` field and uses it to figure out what value to pass.
* **Use `enum` for fixed choices.** If an argument must be one of a known set of values, `enum` makes the AI pick from the list instead of guessing.
* **Mark truly required fields as `required`.** Required fields make the AI ask follow-up questions if it doesn't have the information yet.
* **Keep it small.** Skills with 1–3 well-described arguments work better than kitchen-sink schemas with ten optional knobs.

The properties you define here show up as the typed `SkillArgs` parameter in your code. The editor gives you TypeScript autocomplete based on the schema.

### The `context` argument

The second argument to `run` is the `SkillContext` — a snapshot of who the AI is talking to. You don't have to use it, but it's there when you do.

```typescript
interface SkillContext {
  person: {
    id: number;
    first_name: string;
    last_name: string;
    custom_fields: Record<string, unknown>;
    phones: Array<{ id: number; value: string; primary: boolean }>;
    emails: Array<{ id: number; value: string; primary: boolean }>;
    addresses: Array<{
      id: number;
      primary: boolean;
      country: string;
      postal_code: string;
      region: string;
      locality: string;
      street_address: string;
      extended_address: string;
      latitude: number | null;
      longitude: number | null;
    }>;
    tags: string[];
  };
  conversation: {
    id: number;
    created_at: string;
    last_incoming_message_at: string | null;
    messages: Array<{
      id: number;
      body: string;
      direction: 'incoming' | 'outgoing';
      status: string;
      from: string;
      to: string;
      created_at: string;
      message_actions: Array<{ kind: string; action_valid: boolean }>;
    }>;
    flow_state: { status: 'active' | 'completed'; state_data: Record<string, unknown> } | null;
  };
  incoming_message: { body: string; direction: string };
  account: { name: string; slug: string };
}
```

All fields use `snake_case` to match how they come through the API. The editor autocompletes the full shape — you don't need to memorize it.

Common uses:

* Personalize the result: `context.person.first_name`
* Look up a custom field: `context.person.custom_fields['supporter_priority']`
* Read the most recent message: `context.conversation.messages.at(-1)?.body`
* Find the primary ZIP code: `context.person.addresses.find(a => a.primary)?.postal_code`

### Environment variables — secrets and API keys

Never commit API keys or other secrets into Skill code. Instead, configure them in the **Environment** panel on the Skill edit screen.

1. Open your Skill, click **Environment** in the sidebar.
2. Click **Add Variable**, enter a name (uppercase with underscores — e.g. `STRIPE_API_KEY`), and paste the value.
3. Click the checkmark to save. Values are encrypted at rest and never shown in the UI again.

Read them in your code through the third argument:

```typescript
export async function run(
  args: SkillArgs,
  _context: SkillContext,
  env: Record<string, string>
): Promise<Record<string, unknown>> {
  const resp = await fetch('https://api.example.com/v1/lookup', {
    headers: { Authorization: `Bearer ${env.EXAMPLE_API_KEY}` },
  });
  return await resp.json();
}
```

Environment variables are the only way secrets should reach a Skill — they're scoped to the Skill, encrypted, and rotated without code changes.

## The Execution Environment

Code Skills run in an isolated [Deno](https://deno.com) 2.x runtime. If you've written JavaScript or TypeScript for the browser, most of what you know transfers: `fetch`, `URL`, `Response`, `async`/`await`, `JSON`, `Math`, `Date`, `Intl`, and the rest of the web-standard APIs are available.

A few things are deliberately **not** available:

* **Only `fetch` over `https://` is allowed for network access.** Plain `http://` is blocked. `Deno.connect`, `WebSocket`, and the Node.js modules `node:net`, `node:http`, `node:https`, `node:tls`, `node:dgram`, and `node:dns` all throw if you try to use them. This prevents Skills from reaching internal infrastructure or bypassing the egress proxy.
* **No remote imports.** You cannot `import` code from `https://`, `npm:`, or `jsr:` specifiers. Everything you need should be written inline in `skill.ts`.
* **No file system access, no subprocesses, no FFI.**
* **30-second timeout.** A single Skill execution must complete within 30 seconds or it is killed.
* **64KB stdout limit.** The return value must serialize to under 64KB of JSON.

### Logging

`console.log`, `console.warn`, `console.error`, `console.debug`, and `console.info` all work and are captured in the execution log. Log liberally — it's the easiest way to understand what the AI and your Skill are doing.

```typescript
console.log('Looking up word', args.word);
console.warn('Dictionary API returned no phonetic data');
```

Structured logs are supported too. If you pass a single object with `message` and `meta` fields, the `meta` is stored separately so you can filter on it later:

```typescript
console.log({ message: 'Lookup complete', meta: { word: args.word, ms: duration } });
```

### Errors

If your function throws or the return value can't be serialized, the execution is recorded with `status: error` and the error message is shown in the Test/Debug panel and the Logs list. The AI is also told the Skill failed, so it can adjust its reply rather than hallucinating data.

## Testing a Skill

The **Test / Debug** panel on the Skill edit screen lets you run your Skill against real arguments and real person context without having to trigger a full conversation:

1. Pick a person from the selector (this fills in `context.person`).
2. Enter arguments as JSON (e.g. `{"word": "gerrymandering"}`).
3. Click **Run**.

The panel shows the returned value, console output, and how long the execution took. If the arguments don't match your input schema, you'll get a validation error before the Skill runs — the same validation the AI is subject to.

The **Logs** panel shows every execution of the Skill, including production runs inside Flows. Click an execution to see its input, output, and console output.

## Frequently Asked Questions

<details>

<summary><strong>Can one Skill combine content and code?</strong></summary>

Yes. If a Skill has both code and markdown content, the code runs when the AI calls the Skill, and the markdown content is kept alongside as documentation. In practice, most Skills are one or the other.

</details>

<details>

<summary><strong>Can a Skill write data back into Daisychain?</strong></summary>

Not directly — Skills are read-only outbound today. To capture data onto a Person or tag them, use the built-in [Collect Custom Field, Collect Email, or Collect Name tools](flows.md#tools-and-settings-for-intelligence-nodes). You can also write a Code Skill that calls the Daisychain API itself, using an API key stored as an environment variable. Let us know if you have a use case that needs write-back from a Skill.

</details>

<details>

<summary><strong>Can I import an npm package or a library from deno.land?</strong></summary>

No. Skills run in a locked-down environment with remote and npm imports disabled. Everything you need should fit in the single `skill.ts` file. If you find yourself wanting a big library, reach out — we'd rather understand the use case than watch you work around the sandbox.

</details>

<details>

<summary><strong>Can a Skill call our internal API?</strong></summary>

Only if the API is reachable on the public internet over HTTPS. The egress proxy blocks private IP ranges, so Skills cannot reach services that are only reachable from inside your VPC or corporate network.

</details>

<details>

<summary><strong>How do I share a Skill between accounts?</strong></summary>

Each Skill has an **Export** button on the Settings panel that produces a `.zip` containing the Skill's markdown, code, and input schema. You can re-import that `.zip` in another account by clicking **Import** from the Skills list.

</details>
