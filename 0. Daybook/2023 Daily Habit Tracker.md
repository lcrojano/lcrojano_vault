---
Year: 2023
Folder: 0. Daybook
---
``` dataviewjs 
dv.span("** ⌨️ Fast Typing Practice ⌨️ **") 
/* optional ⏹️💤⚡⚠🧩↑↓⏳📔💾📁📝🔄📝🔀⌨️🕸️📅🔍✨ */ 

const calendarData = {
    year: dv.current().year, // (optional) defaults to the current year 
    colors: "pink",
  //  showCurrentDayBorder: true, // (optional) defaults to true
  //  defaultEntryIntensity: 4, // (optional) defaults to 4
  //  intensityScaleStart: 10, // (optional) defaults to the lowest value passed to entries.intensity
  //  intensityScaleEnd: 100, // (optional) defaults to the highest value passed to entries.intensity
    entries: [], // (required) populated in the DataviewJS loop below
}

// DataviewJS loop
for (let page of dv.pages(`"${dv.current().folder}"`)) {
 //dv.span("<br>" + page.file.name)
for (let item of (page.file.lists).where(p => p["Fast Typing"])) {
    // Uncomment for troubleshooting
    // dv.span("<br>" + page.file.name)
    calendarData.entries.push({
        date: page.file.name, // (required) Format YYYY-MM-DD
        intensity: item['Fast Typing'], // (required) the data you want to track, will map color intensities automatically
        content: "⌨️", // (optional) Add text to the date cell
      //  color: "blue", // (optional) Reference from *calendarData.colors*. If no color is supplied; colors[0] is used
        
content: await dv.span(`[](${page.file.name})`) // await dv.span(`[](${page.file.name})`), //for hover preview

    })}
}

renderHeatmapCalendar(this.container, calendarData)

```

``` dataviewjs
const habitName = "Learn Angular"
dv.span(`** 🅰️ ${habitName} 🅰️ **`) 

const calendarData = {
    colors: "blue",
    entries: [],
}

for (let page of dv.pages(`"${dv.current().folder}"`)) {
for (let item of (page.file.lists).where(p => p[habitName])) {
    calendarData.entries.push({
        date: page.file.name, 
        intensity: item[habitName],
        content: await dv.span(`[](${page.file.name})`), //for hover preview

    })}
}

renderHeatmapCalendar(this.container, calendarData)
```

``` dataviewjs
const habitName = "Microsoft Rewards"
dv.span(`** 📎${habitName} 📎 **`) 

const calendarData = {
    colors: "blue",
    entries: [],
}

for (let page of dv.pages(`"${dv.current().folder}"`)) {
for (let item of (page.file.lists).where(p => p[habitName])) {
    calendarData.entries.push({
        date: page.file.name, 
        intensity: item[habitName],
        content: await dv.span(`[](${page.file.name})`), //for hover preview

    })}
}

renderHeatmapCalendar(this.container, calendarData)

```

``` dataviewjs
const habitName = "Read at least 40 pages of a book"
dv.span(`** 📎${habitName} 📎 **`) 

const calendarData = {
    colors: "greenGithub",
    entries: [],
}

for (let page of dv.pages(`"${dv.current().folder}"`)) {
for (let item of (page.file.lists).where(p => p[habitName])) {
    calendarData.entries.push({
        date: page.file.name, 
        intensity: item[habitName],
        content: await dv.span(`[](${page.file.name})`), //for hover preview

    })}
}

renderHeatmapCalendar(this.container, calendarData)

```