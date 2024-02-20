This script will calculate the diff between two given dates. Use the third parameter of the function to specify the unit of the result. e.g. `days`, `months` or `years`.
```space-script

silverbullet.registerFunction("dateDiff",(date1,date2,unit="days") => {
    const d1=Temporal.PlainDate.from(date1)
    const d2=Temporal.PlainDate.from(date2)
    const diff=d1.until(d2)
    return diff.total({unit,relativeTo:date1})
})

```

## Examples
```template
last week to today: {{dateDiff(lastWeek(),today())}} days
```

```template
Linus Torvalds is {{dateDiff("1969-12-28",today(),"years")}} years old
```
