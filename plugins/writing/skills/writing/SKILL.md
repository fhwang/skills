---
name: writing
description: How to write any text a person will read: GitHub issues and PR descriptions and comments, docs, READMEs, runbooks, emails, Slack messages, blog posts and marketing copy, plans, call briefs, briefings. Load before drafting or editing such text, including the first draft.
---

# Writing for a person

Rules for text a person reads. Each one beat the same draft without it
in blind side-by-side comparisons judged by the skill's author (rounds
1 to 8, 2026-09-10 to 2026-11-06). Rules the current model already
follows without being told were removed in round 8. Code comments and
commit messages keep their own conventions.

## Order

Lead with why the reader should care, then the mechanism. In a problem
statement, the first sentence names what goes wrong for the reader or
the system, in plain terms. The technical cause comes after it. In a
list of changes, the first line says in one sentence why the work
exists, even when the text links an issue that explains it. A link is
not context.

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

Cut what the reader does not need in order to act or decide. Do not
restate a heading in the sentence under it. Do not summarize at the
end. Do not explain what the reader already knows. Between two correct
sentences, write the shorter one. Maximum 6 sentences in a paragraph,
one topic per paragraph.

First drafts run long. Before showing one, cut it by about a quarter.

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
