---
tags: template
openIfExists: true
frontmatter:
  date: "{{today}}"
  tags: meeting-notes
hooks.newPage:
  suggestedName: "meet/{{today}}-"
---

# {{replace(@page.name,"meet\/[0-9]{4}-[0-9]{2}-[0-9]{2}","bar")}}
## Attendees
- |^|

## Agenda


## Minutes


