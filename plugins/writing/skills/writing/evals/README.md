# Writing evals

This directory is the method behind `../SKILL.md`. Every rule in the
skill beat the same draft without it in a blind side-by-side comparison
judged by a person. Use the method here to test a change to the skill,
or to check the skill again when the default model changes.

The texts that were judged are not published. Most were the author's
own issues, PRs, emails and notes, and the rest name a real company.
The results are below and in `rules.json`.

## Files

- `extract-brief.md`: the system prompt that reduces a source text to a
  facts-only brief. The brief is the input to every regeneration, so
  the content stays fixed and only the prompt varies.
- `rules.json`: each rule the skill has carried, where it came from,
  and the rounds that tested it. A rule with no evidence came from a
  note and never faced a round of its own. A rule with a `removed`
  field is no longer in the skill, and the field says which round took
  it out and why.
- `tells.json`: patterns for phrases the judge flagged, each with the
  note it came from.

## How a round works

1. Collect units: short texts of one section each, from real work. Run
   each through `extract-brief.md` to get its brief, and write one
   `context` line naming the reader and the purpose.
2. Choose a control prompt and a challenger prompt. The control is the
   current skill text. The challenger changes one thing.
3. For each unit, build a system prompt from the prompt text and the
   unit's genre and context. Send the brief on stdin to
   `claude -p --model <id> --tools "" --output-format json`, once per
   prompt. Record the model ID from the `modelUsage` key in the output.
4. Run the tells check over every generated text. A hit is a regression
   that needs no judging.

   ```sh
   jq -r '.[].pattern' tells.json | grep -E -n -i -f - <texts>
   ```

5. Add a few anchor pairs: a winning text from an earlier round against
   the challenger's text for the same unit. A challenger that loses an
   anchor pair made that unit worse.
6. Show each pair side by side, blind, with the sides randomized per
   unit and the anchor pairs mixed in. The judge picks left, right, or
   tie, and can attach a note to the pair or to a selected passage.
7. Record every judgment with both texts, which prompt wrote which
   side, the pick, and the notes. Read the picks and the notes, revise
   the challenger, and run again.

To test a single rule, use pairs of the same passage that differ only
in that rule, written by hand or by applying the rule as an edit to a
no-skill draft. Mix several rules in one round, a few pairs each, so
the judge cannot tell which rule a pair tests.

A round with an unknown model cannot be compared with a round on a
known model. Report it as its own group.

## When the default model changes

A rule corrects something a model did by default, and a newer model can
stop doing it. Before adding a rule, run these with the new model:

1. The new model with no skill against the new model with the skill.
2. For each rule, a no-skill draft against the same draft edited by
   that rule alone. A rule that no longer wins comes out.

Round 8 did this for Opus 5.5 and removed half the skill.

## LLM judge

No LLM judge stands in for the person's picks. Opus 5.5 with no skill
text judged the 38 non-tie pairs of rounds 3 and 4b in both orders. It
agreed with the person on 62% of calls, against a bar of 80%. Always
picking the prompt that became the skill agrees on 66%.

## Results

| Round | Date | Model | Test | Result |
|---|---|---|---|---|
| 1 | 2026-09-10 | unknown | A, the ASD-STE100 rule list, against B, a reader-first draft with no word rules | A 3, B 1, tie 7 |
| 2 | 2026-09-11 | unknown | C, A plus concrete words and scannable structure, against A | C 1, A 1, tie 9 |
| 3 | 2026-09-11 | unknown | D, C plus order and names, against C | D 12, C 8, tie 6 |
| 4b | 2026-09-11 | unknown | D against X, a colleague voice with exemplars, a tell list and an editor pass | D 14, X 6, tie 7 |
| 5 | 2026-09-13 | unknown | the same passages with and without an opening count | no count 10, count 0 |
| 6 | 2026-10-12 | unknown | four corrections from real use, three hand-edited pairs each | trim 2-0-1, prose 2-0-1, live-call lines 3-0, one-paragraph intro 0-3 |
| 7 | 2026-11-06 | claude-opus-5-5 | the skill against no skill and four published writing skills | skill 16, others 12, tie 7 |
| 8 | 2026-11-06 | claude-opus-5-5 | no skill against no skill plus one rule | see below |

Round 7, the skill against each challenger (skill, other, tie):

| Challenger | Result |
|---|---|
| No skill | 5-4-1 |
| clean-writing | 4-4-2 |
| Every's Hemingway | 4-2-4 |
| Every's Send Weekly Update and Email Ghostwriter | 3-2-0 |

Round 8, each rule applied alone to a no-skill draft (rule, no skill,
tie):

| Rule | Result | Kept |
|---|---|---|
| Order | 2-0-0 | yes |
| Scannable structure | 2-0-1 | yes |
| Length | 1-0-1 | yes |
| Numbers | 1-0-1 | yes |
| Names | 0-0-1 | no |
| Direct sentences | 1-2-0 | no |
| Live-call lines | 0-2-0 | reworded |
| Concrete words, address | changed no draft | no |

The live-call edit cut spoken questions into fragments, so the rule now
keeps a question whole. That wording is untested.
