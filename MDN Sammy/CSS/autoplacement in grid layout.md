tags: #css 
###### reference 
https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Auto-placement_in_CSS_Grid_Layout

#### default rules for auto placement
- the default flow is to arrange items by row
- grid will lay an item out into each cell of row 1
- If you have created additional rows using the `grid-template-rows` property then grid will continue placing items in these rows
##### sizing rows in the implicit grid
- the default for automatically created rows in the implict grid is for them to be **auto-sized**
- you can however control the size of these rows with the property `grid-auto-rows`
##### sizing rows using `minmax()`
- you can use  [`minmax()`](https://developer.mozilla.org/en-US/docs/Web/CSS/minmax) in your value for [`grid-auto-rows`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-rows) enabling the creation of rows that are a minimum size but then grow to fit content if it is taller
``` css
.wrapper
{
	display:grid;
	grid-template-columns: repeat(3, 1fr);
	gap: 10px;
	grid-auto-rows: minmax(100px, auto)

}
```
##### sizing rows using a track listing
- you can also pass in a track listing, this will repeat
- the following track listing will create an initial implicit row track as 100px pixels and a second as 200px
``` css
.wrapper {
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	gap: 10px;
	grid-auto-rows: 100px 200px;


}
```
##### auto-placement by column
- you can also ask grid to auto-place items by column
	- using the property [`grid-auto-flow`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-flow) with a value of `column`
- in this case grid will add items in rows that you have defined using `grid-template-rows`
- when it fills up a column it will move onto the next explicit column, or create a new column track in the implicit grid
- you can control the size of implicit column tracks with  [`grid-auto-columns`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-columns)
- `grid-auto-column` -> kind of a width property
#### the order of auto placed items
###### filling in the gaps
- sometimes we are laying things out that don't have a logical order and we would like to create a layout that doesn't have gaps in it
- to do this, add the property `grid-auto-flow` witha  value of `dense` to the container