---
tags: template
hooks.snippet:
  slashCommand: tags-highscore
---

```template
{{#each {tag select name where parent != "builtin" order by name}}}
{{#let @tag_name = name}}
[[{{name}}|🏷️ {{name}}({{count({tag where name = @tag_name})}})]] {{/let}}
{{/each}}
```