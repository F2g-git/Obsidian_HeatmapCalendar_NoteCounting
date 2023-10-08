# Obsidian HeatmapCalendar Note Counting
This little script allows me to include a heatmap, much in the style of github, that shows me how many notes i created each day.

It uses the [Obsidian heatmmap calendar](https://github.com/Richardsl/heatmap-calendar-obsidian) and [Obsidian Dataview](https://github.com/blacksmithgu/obsidian-dataview).
As a preparation i use the obsidian [Update Time on Edit](https://github.com/beaussan/update-time-on-edit-obsidian/releases), that gives me a `created` field in the properties of every file I create. 

I had originally forseen to use `dv.view()` from Dataview but unfortunately it does not render the calender. Anyway, i have a script that you could use, if you figure out how to make it render. It is in heatMap.js.

To use it as is, just copy the content of view.md into a note.
