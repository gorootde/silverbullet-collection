---
description: Adds a Banner to tagged pages
banner: "https://upload.wikimedia.org/wikipedia/commons/e/e3/Che_ne_saj.jpg"
tags: template
hooks.top:
  where: 'banner'
  order: 0
---
![banner | 400x300 ]({{@page.banner}})
