---
name: typo-tolerant-input
description: Automatically detect and understand English spelling mistakes in user messages without stopping to ask a clarifying question, unless the intended word is genuinely ambiguous. Use this skill on every incoming user message before processing the request.
---

# Typo-Tolerant Input Skill

## Purpose
Users often make spelling mistakes while typing quickly. Instead of asking
"did you mean X?" every time, this skill lets the agent silently understand
the intended word and continue the task, only asking a question when the
correction is genuinely uncertain.

## Instructions

1. **Scan first, act second.** Before responding to any user message, scan
   it for likely English spelling mistakes (typos, missing letters, swapped
   letters, doubled letters, common phonetic misspellings).

2. **Infer using context.** Use the surrounding sentence and the overall
   conversation topic to figure out the most likely intended word. A
   misspelled word should be interpreted the way a fluent human reader
   would naturally read it, not flagged as an error.

3. **Apply a confidence rule:**
   - **High confidence** (the correction is obvious from context and
     spelling similarity) → silently treat the message as if it were typed
     correctly. Do not comment on the typo. Do not ask for confirmation.
   - **Medium confidence** (a reasonable correction exists but it's worth
     noting) → proceed with the task, and optionally add a short one-line
     note at the end, e.g. "(assuming you meant: receive)".
   - **Low confidence** (two or more equally likely corrections that would
     change the task in different ways) → ask exactly ONE short
     clarifying question, then proceed once answered.

4. **Never block the task on a typo.** Spelling mistakes should never be a
   reason to stop, refuse, or delay completing the user's request.

5. **Common typo patterns to check for:**
   - Transposed letters: `wich` → `which`, `teh` → `the`
   - Missing letters: `adress` → `address`, `recieve` → `receive`
   - Doubled/missing double letters: `comitted` → `committed`
   - Phonetic misspellings: `definately` → `definitely`
   - Missing spaces / merged words: `alot` → `a lot`

6. **Preserve intentional spellings.** Do not "correct" proper nouns, brand
   names, usernames, code identifiers, file paths, or words the user has
   used consistently before — these are very likely intentional and should
   be left untouched.

7. **Logging (optional).** If the agent has a memory/log capability, it may
   silently keep a short list of corrections made in a session for
   transparency, but should not surface this list unless the user asks.

## Example

**User input:** "can u chek if the fil was recieved corectly"

**Agent behavior:** Understands this as "can you check if the file was
received correctly" and proceeds to check the file — no clarifying
question asked.

**User input:** "book a flite to Georgia" (could mean the US state or the
country)

**Agent behavior:** This is a low-confidence case — the correction itself
is easy ("flite" → "flight") but the destination is genuinely ambiguous,
so the agent asks: "Did you mean Georgia (the country) or Georgia, USA?"
