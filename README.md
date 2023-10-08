# Obsidian HeatmapCalendar Note Counting
This little script allows me to include a heatmap, much in the style of github, that shows me how many notes i created each day.

It uses the [Obsidian heatmmap calendar](https://github.com/Richardsl/heatmap-calendar-obsidian) and [Obsidian Dataview](https://github.com/blacksmithgu/obsidian-dataview).
As a preparation i use the obsidian [Update Time on Edit](https://github.com/beaussan/update-time-on-edit-obsidian/releases), that gives me a `created` field in the properties of every file I create. 

I had originally forseen to use `dv.view()` from Dataview but unfortunately it does not render the calender. Anyway, i have a script that you could use, if you figure out how to make it render. It is in heatMap.js.

To use it as is, just copy the content of view.md into a note. You can also customize this.

## Customization
You can change the folders to be read for the calendar view by changing it here:
```js
const docs = dv.pages('"" and -("Excalidraw" and "_ressources" and "_templates")');
```
All folders in `-()` are excluded from the calendar. 
```js
if (value >1){
  calendarData.entries.push({
      date: key,     // (required) Format YYYY-MM-DD
      intensity: value, // (required) the data you want to track, will map color intensities automatically
      color: 'green'
  });
}
```
I use the if clause to prevent lighting up every day, as I have daily notes for every day so far, and those would just clog up my view.

## Example
I have used Joplin for about a year and now use Obsidian since August, hence I still have only a few notes.
![grafik](https://github.com/MsgtGreer/Obsidian_HeatmapCalendar_NoteCounting/assets/50106495/c9c2ee56-cfb0-423f-8f04-f2df4e702104)
