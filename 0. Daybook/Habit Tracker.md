


``` dataviewjs 
dv.span("** ⌨️ Fast Typing Practice **") 
/* optional ⏹️💤⚡⚠🧩↑↓⏳📔💾📁📝🔄📝🔀⌨️🕸️📅🔍✨ */ 

const calendarData = {
    year: 2023, // (optional) defaults to the current year 
    colors: {
        // (optional) defaults to green
        blue: ["#8cb9ff", "#69a3ff", "#428bff", "#1872ff", "#0058e2"],

        // first entry is considered default if supplied
        green: ["#c6e48b", "#7bc96f", "#49af5d", "#2e8840", "#196127"],

        red: ["#ff9e82", "#ff7b55", "#ff4d1a", "#e73400", "#bd2a00"],

        orange: ["#ffa244", "#fd7f00", "#dd6f00", "#bf6000", "#9b4e00"],

        pink: ["#ff96cb", "#ff70b8", "#ff3a9d", "#ee0077", "#c30062"],

        orangeToRed: ["#ffdf04", "#ffbe04", "#ff9a03", "#ff6d02", "#ff2c01"]
    },
    showCurrentDayBorder: true, // (optional) defaults to true
    defaultEntryIntensity: 4, // (optional) defaults to 4
    intensityScaleStart: 10, // (optional) defaults to the lowest value passed to entries.intensity
    intensityScaleEnd: 100, // (optional) defaults to the highest value passed to entries.intensity
    entries: [], // (required) populated in the DataviewJS loop below
}

// DataviewJS loop
for (let page of dv.pages('"0. Daybook"')) {

for (let item of (page.file.lists).where(p => p["Fast Typing"])) {
    // Uncomment for troubleshooting
   // dv.span("<br>" + page.file.name)
    
    calendarData.entries.push({
        date: page.file.name, // (required) Format YYYY-MM-DD
        intensity: item['Fast Typing'], // (required) the data you want to track, will map color intensities automatically
        content: "⌨️", // (optional) Add text to the date cell
        color: "blue", // (optional) Reference from *calendarData.colors*. If no color is supplied; colors[0] is used
    })}
}

renderHeatmapCalendar(this.container, calendarData)

```


``` dataviewjs 
dv.span("** 🅰️ Angular Practice **") 
/* optional ⏹️💤⚡⚠🧩↑↓⏳📔💾📁📝🔄📝🔀⌨️🕸️📅🔍✨ */ 

const calendarData = {
    year: 2023, // (optional) defaults to the current year 
    colors: {
        // (optional) defaults to green
        blue: ["#8cb9ff", "#69a3ff", "#428bff", "#1872ff", "#0058e2"],

        // first entry is considered default if supplied
        green: ["#c6e48b", "#7bc96f", "#49af5d", "#2e8840", "#196127"],

        red: ["#ff9e82", "#ff7b55", "#ff4d1a", "#e73400", "#bd2a00"],

        orange: ["#ffa244", "#fd7f00", "#dd6f00", "#bf6000", "#9b4e00"],

        pink: ["#ff96cb", "#ff70b8", "#ff3a9d", "#ee0077", "#c30062"],

        orangeToRed: ["#ffdf04", "#ffbe04", "#ff9a03", "#ff6d02", "#ff2c01"]
    },
    showCurrentDayBorder: true, // (optional) defaults to true
    defaultEntryIntensity: 4, // (optional) defaults to 4
    intensityScaleStart: 10, // (optional) defaults to the lowest value passed to entries.intensity
    intensityScaleEnd: 100, // (optional) defaults to the highest value passed to entries.intensity
    entries: [], // (required) populated in the DataviewJS loop below
}

// DataviewJS loop
for (let page of dv.pages('"0. Daybook"')) {

for (let item of (page.file.lists).where(p => p["Learn Angular"])) {
    // Uncomment for troubleshooting
   // dv.span("<br>" + page.file.name)
    
    calendarData.entries.push({
        date: page.file.name, // (required) Format YYYY-MM-DD
        intensity: item['Learn Angular'], // (required) the data you want to track, will map color intensities automatically
        content: "🅰️", // (optional) Add text to the date cell
        color: "blue", // (optional) Reference from *calendarData.colors*. If no color is supplied; colors[0] is used
    })}
}

renderHeatmapCalendar(this.container, calendarData)

```


``` dataviewjs
const weekData = {
    year: 2022,
    week: 25,
    habits: [
        {
            colors: ["#c6e48b", "#49af5d"],
            name: "iRacing",
            entries: [
                {
                    date: "2022-06-26",
                    value: 30
                },
                {
                    date: "2022-06-21",
                    value: 45
                }
            ]
        },
        {
            colors: ["#49af5d", "#c6e48b"],
            name: "Language",
            entries: [
                {
                    date: "2022-06-23",
                    value: 30
                }
            ]
        }
    ]
}

renderHabitTracker(this.container, weekData)

```