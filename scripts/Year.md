---
tags: template
---
# Year
This space script will add a template function that returns the year of a given date.

```space-script
silverbullet.registerFunction("year",(date) => {
  const plainDate = Temporal.PlainDate.from(date)
  return plainDate.year
})
```

## Example

```template
 {{year(today())}}
```

