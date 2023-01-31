tags: #css 

##### naming lines when defining a grid
- you can assign some or all of the lines in your grid a name when you define your grid with the `grid-template-rows` and `grid-template-columns` properties
``` css
.wrapper {
	display: grid;
	grid-template-columns: [main-start] 1fr [content-start] 1fr [content-end] 1fr [main-end];
	grid-template-rows: [main-start] 100px [content-start] 100px [content-end] 100px [main-end];
}
```
- once the lines have names, we can use the names to place the item rather than the line number
``` css

.box1 {
	grid-column-start: main-start;
	grid-row-start: main-start;
	grid-row-end: main-end;
}
.box2 {
	grid-column-start: content-end;
	grid-row-start: main-start;
	grid-row-end: content-end;
}
.box3{
	grid-column-start: content-start;
	grid-column-end: main-end;
	grid-row-start: content-end;
}
.box4{
	grid-column-start: content-start;
	grid-column-end: main-end;
	grid-row-start: content-end;
}
```
``` html
<div class='wrapper'>
	<div class='box1'>One</div>
	<div class='box2'>Two</div>
	<div class='box3'>Three</div>
	<div class='box4'>Four</div>
</div>
```

###### giving lines multiple names
- you may want to give a line more than one name
- you can addo this by adding the names inside the square brackeys with whitespace between them
- `[sidebar-end main-start]`

##### implicit grid areas from named lines
- if you append `-start` and `-end` to the lines around an area, grid will create you a named area of the main name used
- imagine having `content-start` and `content-end` both for rows and columns
	- this neans you have a grid area name `content`
``` css
.wrapper {
	display: grid;
	grid-template-columns: [main-start] 1fr [content-start] 1fr [content-end] 1fr [main-end];
	grid-template-rows: [main-start] 100px [content-start] 100px [content-end] 100px [main-end];
}
.thing {
	grid-area: content;
}
```
``` html
<div class='wrapper'>
	<div class='thing'>I am placed in an area named content.</div>
</div>
```

##### implicit grid lines from named areas
- we have seen how named lines create a named area, and this also works in reverse
- named template areas create named lines that you can use to place your items
- we have named areas created using the `grid-area` property, then a layout created in `grid-template-areas`. 
- the area names are:
	- `h`
	- `f`
	- `m`
	- `s`
- this gives us column and row lines:
	- `h-start` and `h-end`
	- `s-start` and `s-end`
	- `m-start` and `m-end`
	- `f-start` and `f-end`

<figure style='background-color:white;'>
	<img src='https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Layout_using_Named_Grid_Lines/5_multiple_lines_from_areas.png'>
</figure>
- To position `overlay` using these implicit named lines is the same as positioning an item using lines that we have named.
``` css
/* ------- */
/* Bunch of code laying the ground for the grid layout*/
/* ---- --*/

.wrapper > div.overlay {
	z-index:10;
	grid-column: main-start / main-end;
	grid-row: h-start / h-end;
	
}
```

##### multiple lines wuth the same name with `repeat()`
- If you do use the repeat syntax you will end up with multiple lines that have the same name, however this can be very useful too.
###### twelve-column grid using `repeat()`
- in this next example you have a grid with twelve equal width columns
- we will end up with a grid that has 12 column lines all name `col-start`
``` css
.wrapper{
	display: grid;
	grid-template-columns: repeat(12, [col-start] 1fr);
}
```
- once you haved created the grid, you can place items onto it
- to place a item from the frist line named col-start to the 5th, we can use
``` css
.item1 {
	grid-column: col-start / col-start 5;
}
```
- you can also use the `span` keyword here
- the next item will be placed from the 7th line named `col-start` and span 3 lines
``` css
.item2 {
	grid-column: col-start 7 / span 3;
}
```

###### defining named lines with a track list
- the repeat syntax can also take a track list, it doesn't just need to a be a single track size that is being repeated
- the code below would create an eight track grid, with a narrower `1fr` width column named `col1-start` followed by a wider `3fr` column named `col2-start`
``` css
.wrapper {
	grid-template-columns: repeat(4, [col1-start] 1fr [col2-start] 3fr)
}
```
- if your repeating syntax puts two lines next to each other then they will be merged
``` css
.wrapper {
	grid-template-columns: repeat(4, [col-start] 1fr [col-end])
}
```