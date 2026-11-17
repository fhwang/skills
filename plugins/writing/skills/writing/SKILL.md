---
name: writing
description: How to write any text a person will read: GitHub issues and PR descriptions and comments, docs, READMEs, runbooks, emails, Slack messages, blog posts and marketing copy, plans, call briefs, briefings. Load before drafting or editing such text, including the first draft.
---

# Writing for a person

Rules for text a person reads. Each one beat the same draft without it
in blind side-by-side comparisons judged by the skill's author (rounds
1 to 8, 2026-09-10 to 2026-11-06), except where a rule says it came
from the author's own edits. Rules the current model already follows
without being told were removed in round 8. Code comments and commit
messages keep their own conventions.

## Order

Set up the situation before the stakes. Open with how the thing
normally works, or the practice it should follow. Then say what goes
wrong, then what follows from it: "So anyone who can reach the
endpoint can…". Urgency belongs in the title or a label such as
"Severity: Critical", not in a dramatic first sentence. Say what was
observed, then what you infer from it and how sure you are. In a list
of changes, the first line says in one sentence why the work exists,
even when the text links an issue that explains it. A link is not
context.

## Scannable structure

The first sentence of each section states the finding, the decision,
or the instruction. Detail follows in the order the reader will use
it. Parallel items go in a list, and nothing else does. Each item
opens with the thing it is about, and bold, if any, covers only those
first words. A status update or an email of a few sentences reads
better as prose. Numbers that belong together go in one line or a
small table, never spread across sentences. A reader who reads only
the first sentence of each section and the first words of each list
item gets the whole picture.

## Length

Cut whole sentences the reader does not need in order to act or
decide; don't squeeze the sentences you keep. Do not restate a heading
in the sentence under it. Do not summarize at the end. Do not explain
what the reader already knows. Maximum 6 sentences in a paragraph, one
topic per paragraph.

Name things in full: "the Release workflow", not "Release"; "this PR
adds", not "this adds"; "whether the workspace is paid or free", not
"whether it pays". Shorthand the reader has to decode costs more than
the words it saves.

Don't write to persuade. Cut sentences whose job is to make a problem
sound alarming or a choice look obvious: "a false drop to zero",
"nothing would ever flag it", "we'll never have to announce it".

Text the user reads during a live call, such as a call brief, is short
lines to glance at between answers. A question the user will ask stays
a full question, worded the way the user would say it aloud.

## Numbers

Put a number in the text where it changes what the reader does. Where
it does not, write "most", "a few", or drop it.

Do not count the items you are about to list. A heading, a standfirst,
or a section's first sentence names the finding, not how many items sit
under it. Write "Routing a new fact", not "Five questions, asked in
order". The reader takes the count from the list. This holds when the
count is accurate and when the list is long.

## What the comparisons showed

- From the author's own edits (November 2026): asked to rewrite drafts
  they had sent unedited, for voice only, the author moved the stakes
  after the setup in 4 of 8 changed blocks, spelled out shorthand in 5,
  and cut persuasive sentences in 4. The earlier rules "lead with why
  the reader should care", "write the shorter one" and "cut by a
  quarter" produced the openings they rewrote, so those rules were
  replaced.
- Judge and revise text in units of one section. Long samples tie.
- Source wording survives instructions. When rewriting a text that
  already carries jargon, translate the jargon in a separate pass.
- A blog post, proposal, or README can take a few paragraphs to set up
  the problem. A one-paragraph intro lost 0 to 3 in round 6.
- Removed in round 8 because Opus 5.5 already follows them with no
  skill: concrete words, quoting literal strings, and "you" for the
  user. The ban on "load-bearing" lives on in `evals/tells.json`.
- Removed in round 8 because they made text worse: the sentence rules
  (simple tenses only, few modals, no semicolons). They turned "haven't
  opened" into "did not open".
