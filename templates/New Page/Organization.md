---
tags:
  - template
hooks.newPage:
  suggestedName: "organization/"
  forPrefix: "organization/"
openIfExists: true
frontmatter:
  tags:
    - organization
---
---

# {{replace(@page.name,"organization/","")}}
- |^|
