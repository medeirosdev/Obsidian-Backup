tags: #css 
- the grid is indexed according to the writing mode of the document

##### positioning items by line number
- we would like the first item to start on the far left of the grid and span a single column track
- note that we can leave empty cells if we wish
``` css
.box1
{
	grid-column-start:1;
	grid-column-end: 2;
}
```

##### the `grid-column` and `grid-row` shorthands
``` css
.box1
{
	grid-column: 1 / 2;
	grid-row: 1 / 4;
}
```

##### default spans
- If an item only spans one track you can omit the `grid-column-end` or `grid-row-end` value
- grid defaults to spanning one track
``` css
.box1
{
	grid-column-start: 1;
	grid-row-start: 1;
	grid-row-end: 4;
}
.box2{
	grid-column-start: 3;
	grid-row-start: 1;
	grid-row-end: 3;
}
```
###### default spans with shorthand placement
- our shorthand would look like the following code
``` css
.box1{
	grid-column: 1;
	grid-row: 1 / 4;
}
.box2 {
	grid-column: 3;
	grid-row: 1 / 3;
}
.box3 {
	grid-column: 2;
	grid-row: 1;
}

```

##### the `grid-area` property
- we can define each area with a single property - `grid-area`
- the order of the values for grid-area are as follows
	- `grid-row-start`
	- `grid-column-start`
	- `grid-row-end`
	- `grid-column-end`
``` css
.box1 {
	grid-area: 1 / 1/ 4 / 2;
}
.box2 {
	grid-area: 1 / 3 / 3 / 4;
}
.box3 {
	grid-area: 1 / 2 / 2 / 3;
}
.box4 {
	grid-area: 3 / 2 / 4 / 4;
}
```

##### counting backwards
- These lines can be addressed as `-1`, and you can count back from there – so the second last line is `-2`
``` css

.box1 {
	grid-column-start: -1;
	grid-column-end: -2;
	grid-row-start: -1 / -4;
}

.box2{
	grid-column-start: -3;
	grid-column-end: -4;
	grid-row-start: -1;
	grid-row-end: -3;
}
```
###### stretching an item across the grid
``` css
.item
{
	grid-column: 1 / -1;
}
```
#### using the `span` keyword
``` css
.box1 {
	grid-column: 1;
	grid-row: 1 / span 3;
}
.box2 {
	grid-column: 3;
	grid-row: 1 / span 2;
}
```
- you can also use the `span` keyword in the value of `grid-row-start/grid-row-end` and `grid-column-start/grid-column-end`
- the following two examples will create the same grid area
- this example, first we set the start row line, then the end line explain that we want to span 3 lines. 
	- the area will start at line 1 and span 3 lines to line 4
``` css
.box1 {
	grid-column-start: 1;
	grid-row-start: 1;
	grid-row-end: span 3;
}
```
- this second example, we specify the end row line we want the item to finish at and then set the start line as `span 3`
	- this means the item will need to span upwards from the specified row line
	- the area will start at line 4 and span 3 lines to line 1
``` css
.box1 {
	grid-column-start: 1;
	grid-row-start: span 3;
	grid-row-end: 4;
}
```