```dataviewjs
const dateField = 'created';
const docs = dv.pages('"" and -("Excalidraw" and "_ressources" and "_templates")');

function parseDateField(page){	
	var date = page[dateField];
	if (moment.isDate(date)){
		return date;
	};
	if (typeof date === 'string' || date instanceof String){
		return moment(date);
	};
	if (date instanceof DateTime){
		//console.log("Is Date Time");
		return moment(date.toString());
	}
	if (typeof(date)=='undefined'){
		//console.log(date);
	}
	//console.log(date);
	//console.log(page.file.name);
	//Notes that dont have a 'created' property end up here:
	return moment('1900-01-01');	
}

function countNotesAtDate(){
	var created_date;
	var dailyDict = [];
	for (var page of docs){	
		
		created_date = parseDateField(page).format('YYYY-MM-DD');
		//console.log(created_date);
		if (created_date in dailyDict){
			dailyDict[created_date] += 1;
		} else{
			dailyDict[created_date] = 1;
		}
	}
	return dailyDict;
}

// creating the table
var dailyDict = countNotesAtDate();

const calendarData = {
    year: 2023,  // (optional) defaults to current year
    colors: {    // (optional) defaults to green
        blue:        ["#8cb9ff", "#69a3ff", "#428bff", "#1872ff", "#0058e2"], // first entry is considered default if supplied
        green:       ["#333333","#c6e48b", "#7bc96f", "#49af5d", "#2e8840", "#196127"],
        red:         ["#ff9e82", "#ff7b55", "#ff4d1a", "#e73400", "#bd2a00"],
        orange:      ["#ffa244", "#fd7f00", "#dd6f00", "#bf6000", "#9b4e00"],
        pink:        ["#ff96cb", "#ff70b8", "#ff3a9d", "#ee0077", "#c30062"],
        orangeToRed: ["#ffdf04", "#ffbe04", "#ff9a03", "#ff6d02", "#ff2c01"]
    },
    showCurrentDayBorder: false, // (optional) defaults to true
    defaultEntryIntensity: 0,   // (optional) defaults to 4
    intensityScaleStart: 2,    // (optional) defaults to lowest value passed to entries.intensity
    intensityScaleEnd: 10,     // (optional) defaults to highest value passed to entries.intensity
    entries: [],                // (required) populated in the DataviewJS loop below
}

for (const [key,value] of Object.entries(dailyDict)){
    //dv.span("<br>" + page.file.name) // uncomment for troubleshooting
    if (value >1){
	    calendarData.entries.push({
	        date: key,     // (required) Format YYYY-MM-DD
	        intensity: value-1, // (required) the data you want to track, will map color intensities automatically
	        color: 'green'
	    });
    }
}

renderHeatmapCalendar(this.container, calendarData)
```
