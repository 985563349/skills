---
name: writing
description: Use when the user asks to write, outline, or revise a long-form technical article, engineering blog post, or explanatory documentation page.
---

# Writing

Explain a mechanism until it becomes a decision. Start from a failure the reader recognizes, define the terms, show the fix, and end with rules for choosing it. Calm, precise, practical.

## Before writing

When the user asks for a new article, do not draft yet. Offer these choices in the user's language:

> 1. Write now
> 2. Add context
> 3. Ask about the details

If the user chooses add context, ask them to provide it in their own words, wait, then offer the same choices again. Treat the added context as a constraint and update the design tree; do not write yet.

If the request already says "write now" or "no questions", skip the choice and write. If the user asks to revise an existing draft, skip the choice and edit directly.

### Interview rounds

If the user chooses "Ask about the details", interview them in rounds until they choose direct write.

- Model the article as a **design tree**: angle, reader's prior knowledge, scope, structure, examples, depth, length, and constraints. Answers open and close branches.
- A **round** asks the current **frontier**: every decision whose prerequisites are settled. Ask the whole frontier at once, numbered, with your recommended answer. Do not drip questions one at a time unless the user asks for that.
- Format each round:

```
❓ **Q1** - **<title>**: <question body, with options if useful>
➡️ <your recommended answer>

---

❓ **Q2** - **<title>**: <question body, with options if useful>
➡️ <your recommended answer>
```

Use these markers only in interview rounds, never in the article.

- Word each question so "yes" accepts the recommendation. Skip anything the user already answered.
- Wait for the answers. Do not write between rounds.
- A question that depends on another question still open belongs to a later round, not this one.
- After each round, offer the choices again: "1. Write now / 2. Add context / 3. More questions."
  - Write now: start the article.
  - Add context: ask for it, wait, then offer the choices again; do not write.
  - More questions: recompute the frontier and ask only the new, unblocked questions.
- If the frontier is empty, say so and offer the choices again; do not invent questions.
- If the user says "write now" in an answer, treat it as the choice and start.
- Treat context the user adds at any point as a constraint; update the tree and do not ask for it again.
- Look up public facts yourself with web, files, or tools. Ask only for decisions, preferences, and private context you cannot know. Do not block unrelated questions on pending research.
- The article starts only when the user chooses direct write. An empty frontier, or enough information, is not permission.

### Start writing

Use the answers as constraints. If a non-essential detail is still unknown, make a reasonable assumption and move on; do not reopen the interview. Once the user chooses direct write, write the article; do not ask for outline approval or another confirmation. If no language is specified, write the article in Chinese.

## Reader and voice

- Reader: working developers. Peer tone; no beginner recap or generic stakes.
- Use "we", never "I". Short declaratives. Explain, don't perform: no hype, jokes, emojis, or marketing adjectives in the article.
- Be confident in definitions, explicit about limits. Prefer concrete states, numbers, queries, and event sequences.
- Gloss technical terms on first use with their full name and plain meaning.

## Article structure

Use this order unless the topic needs another:

1. **Opening.** Three to five real symptoms as questions. One sentence naming their shared cause. A bulleted list of the concepts that resolve them, in order. One sentence naming the practice stack.
2. **Invariant.** Before any mechanism, ask what must remain true. Name it after describing it. Give three to five rules from one realistic system.
3. **Concepts.** One H2 per major concept, H3 for subtypes. Keep one running example domain and reuse its entities. For each: definition, why it exists, a minimal example, and its limit.
4. **Practice.** Apply the concepts to the named stack. Show realistic, typed code with error paths; elide unrelated setup with `...`. State the guarantee it buys and the cost it adds.
5. **Decision rules.** An ordered list from simplest to most complex. Each item: "When X, prefer Y; otherwise Z, at this cost."
6. **Finally.** Two to four short paragraphs that return to the invariant and reframe the mechanisms as tools. No heading recap, no call to action.

## Sentence signatures

- Define before use: "X is...", "X means...", "X describes...".
- One idea per paragraph, one to three sentences. A single sentence may carry a key claim.
- Contrast look-alikes and correct likely misconceptions in one sentence: "A is about..., while B is about..." or "X does not mean Y."
- Qualify implementation-dependent claims with "usually", "may", or "depends on the database". Never generalize one product's behavior to all.
- End a section on its boundary or consequence, not on a transition.

## Formatting signatures

- Short noun-phrase headings; no questions or numbering.
- Bold inline identifiers and key values; keep code examples close to production shape.
- Use blockquotes for caveats that prevent a wrong conclusion, and tables for multi-option comparisons.
- For race conditions, use a plain-text fence with one step per line and aligned `Transaction A` / `Transaction B` labels. Three to six lines.

## Model paragraph

A lock timeout is not a deadlock. A timeout means one transaction waited longer than the configured limit, so the database aborted that wait and returned an error. A deadlock means two or more transactions hold what the others need, so none can proceed. The first is usually a tuning problem. The second is a cycle, and the database must break it by aborting one participant.

## Final check

- Did the user choose (or explicitly request) direct write before drafting, and did I stop asking questions after that?
- Does the opening name real symptoms and the single cause behind them?
- Is every term defined before it is used?
- Does each concept have an example and an explicit limit?
- Does the practice section show the guarantee and its cost?
- Does the ending return to the invariant without repeating the headings?
