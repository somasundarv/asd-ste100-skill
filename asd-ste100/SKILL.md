---
name: asd-ste100
version: 1.0.0
description: |
  Rewrite or draft text in ASD-STE100 Simplified Technical English (the
  aerospace/defense controlled-language standard). Use when the user asks
  for STE, Simplified Technical English, ASD-STE100, a maintenance/ops
  procedure, or technical writing that must be unambiguous for non-native
  English readers and translation/MT pipelines.
license: MIT
compatibility: claude-code
allowed-tools:
  - Read
  - Write
  - Edit
  - Grep
  - Glob
---

# ASD-STE100 (Simplified Technical English)

Rewrite the given text, or draft new text, to ASD-STE100 rules. Apply every
rule below; don't skip ones that feel inconvenient — the standard exists
because skipped rules are where ambiguity creeps back in.

## Writing rules

1. **One instruction or one idea per sentence.** Split compound sentences.
2. **Active voice, not passive.** "Remove the cover" not "The cover is removed."
3. **Simple tenses only** — simple present, simple past, simple future.
   No perfect/progressive tenses ("has been", "is doing").
4. **Imperative mood for instructions.** "Open the valve" not "You should open the valve" / "The valve must be opened."
5. **Max ~20 words per instruction sentence, ~25 for description sentences.** Split longer ones.
6. **Max 3 nouns in a noun cluster.** "fuel pump drive shaft housing bolt" → "bolt on the housing of the fuel pump drive shaft."
7. **No gerunds as nouns.** "the opening of the valve" → "when you open the valve."
8. **-ing words only as adjectives/verbs, never ambiguous modifiers.** Rewrite so it's clear what the -ing word attaches to.
9. **One word, one meaning, one part of speech.** Don't let "close" be both verb and adjective in the same doc — pick the STE-approved sense and stay with it.
10. **Use "this"/"that" + noun to refer back, not bare "it"/"they"** when the referent could be ambiguous. "Remove the filter. Clean this filter." not "Remove the filter. Clean it."
11. **Use articles (a/the) correctly and consistently** — don't drop them to sound terse.
12. **Numbered steps for procedures, one action per step.** Conditions go before the instruction: "If the light is on, press the button" not "Press the button if the light is on."
13. **Approved vocabulary only** — a small general word list (~900 words), each with one fixed meaning. Replace synonyms with the one approved word. Technical/domain nouns (part names, system names) are allowed as-is as "technical names," but use them consistently.

### Common word substitutions

| Avoid | Use |
|---|---|
| utilize, employ | use |
| commence, initiate | start, begin |
| terminate | stop, end |
| prior to | before |
| subsequent to | after |
| in order to | to |
| approximately | about |
| sufficient | enough |
| numerous | many |
| obtain | get |
| assist | help |
| ensure | make sure |
| additional | more |
| however | but |
| therefore | so |
| in the event that | if |

### Banned constructions

- Passive voice: "The switch was turned off by the technician" → "The technician turned off the switch."
- Strings of nouns: "engine oil pressure warning light indicator" → "indicator light for the warning of low oil pressure in the engine."
- Vague quantifiers: "a few", "several", "some" → give the number, or use "some" only where STE permits (no exact count exists).
- Idioms and metaphors: "ballpark figure", "a piece of cake" → plain literal phrasing.
- Contractions: "don't", "it's" → "do not", "it is."

## Procedure

1. Read the source text (or the request, if drafting from scratch).
2. Rewrite sentence by sentence against the rule list above.
3. Re-check every rewritten sentence against the word-count limits and the
   vocabulary table — a rewrite that fixes voice but adds a banned word
   isn't done.
4. If a sentence can't be split cleanly without losing meaning, say so and
   give the best available version — don't silently drop content to hit a
   word count.
5. Output the STE text. If asked to also explain changes, list them after
   the text, not interleaved with it.

## Example

**Before:**
> Prior to commencement of the maintenance procedure, technicians should
> ensure that the aircraft electrical power distribution system has been
> de-energized, as failure to do so could result in serious injury.

**After (STE):**
> Before you start the maintenance procedure, make sure the electrical power
> system of the aircraft is off. If you do not do this, you can get a
> serious injury.
