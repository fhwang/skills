# Skills

Claude Code skills, each tested against the same model with no skill.
A rule stays only while it still beats the model's default.

## writing

Rules for text a person will read: issues, PR descriptions, docs,
runbooks, emails, Slack posts, plans and call briefs. The skill covers
four things the model gets wrong without it:

- **Order:** why the reader should care comes before the mechanism.
- **Scannable structure:** each section opens with its finding, and
  lists hold only parallel items.
- **Length:** cut what the reader doesn't need, and trim a first draft
  by about a quarter.
- **Numbers:** a number appears only where it changes what the reader
  does, and lists don't open by counting their items.

Every rule won blind side-by-side comparisons judged by a person, over
eight rounds from September to November 2026. In round 8, each rule was
applied alone to Opus 5.5 drafts with no skill, and rules the model
already followed or made worse came out. The skill is about 600 words.
[`evals/`](plugins/writing/skills/writing/evals/) has the method and
the results.

## Install

```
/plugin marketplace add fhwang/skills
/plugin install writing@fhwang-skills
```

Or copy `plugins/writing/skills/writing/` into `~/.claude/skills/`.

## License

MIT
