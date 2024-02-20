This is a collection of scripts of basic mathematical functions.

```space-script
silverbullet.registerFunction('ceil',(number) => {
  return Math.ceil(Number(number))
})

silverbullet.registerFunction('floor',(number) => {
  return Math.floor(Number(number))
})

silverbullet.registerFunction('round',(number,digits=1) => {
  return Number(number).toFixed(digits)
})

```



## Examples
```template
{{ceil("4.2")}} = 5

{{floor("3.9")}} = 3

{{round("3.141")}} = 3.1
```
