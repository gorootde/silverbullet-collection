# Days till date
This will add a template function that calculates the number of days from today until a given date.

```space-script
silverbullet.registerFunction("daysTillDate",(date) => {
  const parsedDate = Temporal.PlainDate.from(date)
  const now = Temporal.Now.plainDateISO();
  return now.until(parsedDate, { largestUnit: 'days' }).days
})
```

## Example

```template
{{daysTillDate(nextWeek())}}
```


