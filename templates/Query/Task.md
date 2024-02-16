---
tags: template
description: Generic task template that supports updating the status back in the origin page
---
* [{{state}}] {{#if deadline <= today()}}⚠️OVERDUE⚠️{{else}}📝{{/if}} {{#if deadline}}({{daysTillDate(deadline)}}d){{/if}} [[{{ref}}]] {{name}}