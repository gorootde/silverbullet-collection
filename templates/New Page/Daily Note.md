---
description: "Your daily note template"
tags: template
frontmatter: 
  date: "{{today}}"
hooks.newPage:
  suggestedName: "Journal/Day/{{today}}"
  confirmName: false
  openIfExists: true
  forPrefix: "Journal/Day/"
  command: "Open Daily Note"
  key: "Alt-Shift-d"
---
# Today
* |^|

## Meetings
```query
page where date = @page.date and tags = "meeting-notes" render [[Library/Core/Query/Page]]
```

# New things
- 