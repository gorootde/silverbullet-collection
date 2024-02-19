Adds the command `Insert Date` that can be used to conveniently pick and insert any date

```space-script

silverbullet.registerCommand({name:"Insert Date"},async () => {
  const dayNames=['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']
  const monthNames=['January','February','March','April','May','June','July','August','September','October','November','December']
  
  const now=Temporal.Now.plainDateISO()
  const dateOptions=[
    {name: "Today",date: now},
    {name: "Tomorrow",date: now.add({days: 1})},
    {name: "Day after tomorrow",date: now.add({days: 2})},
    {name: "In one week",date: now.add({weeks: 1})},
    {name: "In two weeks",date: now.add({weeks: 2})},
    {name: "In a month",date: now.add({months: 1})},
    
  ]
  const maxOffset=365
  for(let offset=1;offset<=maxOffset;offset++){
    const date=now.add({days: offset})
    const dayName=dayNames[date.dayOfWeek - 1]
    const monthName=monthNames[date.month-1]
    const name=`${date.year}/${date.month}/${date.day}: ${dayName}`
    dateOptions.push({name,date})
    dateOptions.push({name:`In ${offset} days`,date,orderId: maxOffset+offset})
  }

  const picked=await syscall("editor.filterBox","Pick a date",dateOptions)
  if(picked){
    await syscall("editor.insertAtCursor",picked.date.toString())
  }
})
```



