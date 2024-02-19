Calculates the time between 2 given times. Use the third parameter of the function to specify the unit of the result. e.g. `hour`, `minute` or `second`.

```space-script
silverbullet.registerFunction('timeDiff',(time1,time2,unit='hour') => {
    function parseTime(time){
        const splitted=time.split(":")
        const hour=splitted[0]
        const minute=splitted[1]
        return Temporal.PlainTime.from({hour, minute})
    }
    const t1=parseTime(time1)
    const t2=parseTime(time2)
    const diff=t1.until(t2)
    return diff.total({unit})
})

```template
{{ timeDiff("08:00","15:59") }}
```
