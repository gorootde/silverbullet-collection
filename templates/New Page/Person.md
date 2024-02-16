---
tags:
  - template
hooks.newPage:
  suggestedName: "person/"
  forPrefix: "person/"
openIfExists: true
frontmatter:
  tags:
    - person
  birthday:
  organization:
---

# {{replace(@page.name,"person/","")}}



