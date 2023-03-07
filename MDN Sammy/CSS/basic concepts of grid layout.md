tags: #css 
- css grid layout introduces a two-dimensional grid system to CSS

###### grid container
- we create a grid container by declaring `display: grid` or `display: unline-grid` on an element
###### grid tracks
- we define rows and columns on our grid with the `grid-templa-rows` and `grid-template-columns` properties
- these define grid tracks
- a **grid track** is the space between any two adjacent line on the grid
###### track listing with the `repeat()` function
- large grids with many tracks can use the `repeat()` notation, to repeat all or a section of the track listing
``` css
.wrapper
{
	display: grid;
	grid-template-columns: repeat(3, 1fr);
}
.wrapper-two
{
	display: grid;
	grid-template-columns: 20px repeat(3, 1fr) 40px;
}
.wrapper-three
{
	display: grid;
	grid-template-columns: repeat(5, 1fr 2fr);

}
```

###### implicit and explicit grids
- when using `grid-template-columns` we specifically define our columns tracks, but the grid also creates rows on its own.
	- these rows are part of the implicit grid
- the explicit grid consists of any rows and columns defined with `grid-template-columns` or `grid-template-rows`
- if you place something outside of the defined grid - or due to the amout of content, more grid tacks are needed - then the grid creares rows and columns in the implicit grid
- these tracks will be auto-sized by default, resulting in their size being based on the content that is inside them
- You can also define a set size for tracks created in the implicit grid with the [`grid-auto-rows`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-rows) and [`grid-auto-columns`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-columns)properties
- In the below example, we use `grid-auto-rows` to ensure that tracks created in the implicit grid are 200 pixels tall.

``` css
.wrapper
{
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	grid-auto-rows: 200px;
}
```

###### track sizing and minmax
- when setting up an explicit grid or defining the sizing for automatically created row os columns we may want to give tracks a minimum size, but also ensure they expand to fit any content that is added
	- I may want my rows to neve collapse smaller than 100 pixels, but if my content stretches 300px pixels in height, then I would like the row to stretch to that height
- Grid has a solution for this with the `minmax()` function
``` css
.wrapper
{
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	grid-auto-rows: minmax(100px, auto);

}
```

##### grid lines
- it should be noted that when we define a grid we define the grid tracks, not the line.
	- Grid then give us numbered lines to use when positioning items
	<img src='https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Basic_Concepts_of_Grid_Layout/1_diagram_numbered_grid_lines.png'>

- lines are numbered according to the writing mode of the document
###### positioning items against lines
``` css
.wrapper
{
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	grid-auto-rows:100px;
}
.box1
{
	grid-column-start: 1;
	grid-column-end: 4;
	grid-row-start: 1;
	grid-row-end: 3;
}
```
- line-positioning shorthands
``` css
.box1
{
	grid-column: 1 / 4;
	grid-row: 1 / 3;
}

```

###### grid cell
- a grid cell is the smallest unit on a grid
- conceptually it is like a table cell
###### grid area
- items can span one or more cells both by row or by column, and this creates a _grid area_

###### layering items with z-index
- grid items can occupy the same cell, and in this case we can use the [`z-index`](https://developer.mozilla.org/en-US/docs/Web/CSS/z-index) property to control the order in which overlapping items stack.
``` css
.wrapper{
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	grid-auto-rows: 100px;
}
.box1 {
	grid-column-start: 1;
	grid-column-end: 4;
	grid-row-start: 1;
	grid-row-end: 3
}
.box2{
	grid-column-start: 1;
	grid-row-start: 2;
	grid-row-end: 4;
}
```
- We can control the order in which items stack up by using the `z-index` property - just like positioned items