# `createView`
Group all entries in `data` by `field`. Use `mappings` to aggregate the other fields in the entry.
`mappings` is an array of strings that follow this syntax:
- `sum(fieldname)` Sums up the field value
- `first(fieldname)` Use the value of the first row in the dataset
- `max(fieldname)` Use the (numeric) larger value and overwrite smaller ones
- `min(fieldname)` Use the (numeric) smaller value and overwrite the larger ones

## Example

| Date | TicketID | Effort | Estimate |
| ---- | -------- | ------ | -------- |
| 2024-07-01 | 4567 | 1 | 2 |
| 2024-07-02 | 4567 | 3 | 0 |
| 2024-07-03 | 4568 | 9 | 0 |

`createView({table},"ticketId",["first(ticketId)","sum(effort)","max(estimate)"]`


Will output data that renders to this table:


| TicketID | Effort | Estimate |
| ---- | -------- | ------ | 
| 4567 | 4 | 2 |
| 4568 | 9 | 0 |



```space-script
silverbullet.registerFunction({name:'createView'},(data,field,mappings) => {

  //Parse mapping syntax into an object with the field to be aggregated as property name, and a function that does the aggregation as value. Function will receive the immediate aggregation result as first parameter and the next value to be aggregated on top as second paramter
  function parseMappings(mappings){
    let result={}
    mappings.forEach(mapping => {
      const {groups: {aggregation,fieldname}}=/(?<aggregation>[a-z]+)\((?<fieldname>.+)\)/.exec(mapping)
      
      if(aggregation=="sum"){
        result[fieldname]=(aggregatedValue,nextValue) => aggregatedValue ? aggregatedValue + nextValue : nextValue
      } else if(aggregation=="first"){
        result[fieldname]=(aggregatedValue,nextValue) => aggregatedValue ? aggregatedValue : nextValue
      } else if(aggregation=="min"){
        result[fieldname]=(aggregatedValue,nextValue) => aggregatedValue && aggregatedValue < nextValue ? aggregatedValue : nextValue
      } else if(aggregation=="max"){
        result[fieldname]=(aggregatedValue,nextValue) => aggregatedValue && aggregatedValue > nextValue ? aggregatedValue : nextValue
      } 
    })
    return result
  }
  
  let mapper=parseMappings(mappings)
  //console.log("MAPPER",mapper)
  //Collect rows with same `field`-property values in a list
  let groupedrows={}
  for(const row of data){
    const key=row[field]
    if(!groupedrows[key]){
      groupedrows[key]=[]
    }
    groupedrows[key].push(row)
  }

  //Aggregate each collected list into a new entry
  const result=[]
  for(const [fieldvalue,rows] of Object.entries(groupedrows)){
    const entry={}
    entry[field]=fieldvalue
    for(const row of rows){
      for(const [k,v] of Object.entries(row)){
        
        if(mapper.hasOwnProperty(k)){
          //console.log("KV",k,v)
          entry[k]=mapper[k](entry[k],v)
        }
      }
    }
    result.push(entry)
  }
   //console.log("RESULT",result)
  return result
})
```



