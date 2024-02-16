# Days Till Birthday
This space script will add a function that calculates the days until the next birthday by the given birth date.

```space-script
silverbullet.registerFunction("daysTillBirthday",(date) => {
  const birthDate = Temporal.PlainDate.from(date)
  const now = Temporal.Now.plainDateISO();
  const thisYearBirthday = new Temporal.PlainDate(now.year, birthDate.month, birthDate.day);

  if (now.equals(thisYearBirthday)) {
        return 0; // Happy Birthday!
  } else if (Temporal.PlainDate.compare(now,thisYearBirthday) < 0) {
        // Birthday is still coming this year
        return now.until(thisYearBirthday, { largestUnit: 'days' }).days;
    } else {
        // Birthday has passed for this year, calculate for next year
        const nextYearBirthday = new Temporal.PlainDate(now.year + 1, birthDate.month, birthDate.day);
        return now.until(nextYearBirthday, { largestUnit: 'days' }).days;
    }
})
```

## Example

```template
{{daysTillBirthday("1982-06-20")}}
```

