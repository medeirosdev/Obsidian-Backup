tags: #css 

##### naming a grid area
- we can define an area  by givin it a name and then specify the location of that area in the value of the  [`grid-template-areas`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-areas) property
- with the [`grid-area`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-area) property you can assign each of these areas a name
	- this will not yet create any layout, but we now have named areas to use in a layout
``` css
.header{
	grid-area:h;
}
.footer {
	grid-area:f;
}
.content{
	grid-area: c;
}
.sidebar {
	grid-area: s;
}

```
- having specified these name you can then create your layout
	- this time, instead of placing  your items using line numbers specified on the items themselves
``` css
.wrapper {
	display: grid;
	grid-template-columns: repeat(9, 1fr);
	grid-auto-rows: minmax(100px, auto);
	grid-template-areas: 
	"h h h h h h h h h"
	"s s s m m m m m m"
	"f f f f f f f f f";
}
```
##### leaving a grid cell empty
- You can leave grid cells empty with this method of layout.
- to leave a cell empty use the full stop character '`.`'
``` css
display: grid;
grid-template-columns: repeat(9, 1fr);
grid-template-areas:
	"h h h h h h h h h"
	"s s s m m m m m m"
	". . . f f f f f f";
```
##### redefining the grid using media queries
- As our layout is now contained in one part of the CSS, this makes it very easy to make changes at different breakpoints. You can do this by redefining the grid, the position of items on the grid, or both at once.
``` css
.wrapper {
	display: grid;
	grid-auto-rows: minmax(100px, auto);
	grid-template-columns: 1fr;
	grid-template-areas:
	"h"
	"m"
	"s"
	"f";
}
```
- We can then redefine that layout inside media queries to go to our two columns layout, and perhaps take it to a three column layout if the available space is even wider.
``` css
@media (min-width: 500px)
{
	.wrapper{
		grid-template-columns: repeat(9, 1fr);
		grid-template-areas:
		"h h h h h h h h h"
		"s s s m m m m m m"
		"s s s f f f f f f";
	}
}
@media (min-width: 700px)
{
	.wrapper {
		grid-template-areas:
		"h h h h h h h h h"
		"s s m m m m m f f";
	}
}
```
##### using `grid-template-areas` for UI elements
- Many of the grid examples you will find online make the assumption that you will use grid for main page layout, however grid can be just as useful for small elements as those larger ones
###### media object example
- As a very simple example we can create a "media object". This is a component with space for an image or other media on one side and content on the other. The image might be displayed on the right or left of the box.

<figure>
<img src='https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Grid_Template_Areas/4_media_objects.png'>
</figure>

- Our grid is a two-column track grid, with the column for the image sized at `1fr` and the text `3fr`
- we give the image area a grid area name of `img` and the text area `content`, then we we can lay those out using the `grid-template-areas` property.
``` css

.media 
{
	border:2px dotted blue;
	border-radius: 5px;
	max-width: 400px;
	display: grid;
	grid-template-columns: 1fr 3fr;
	grid-template-areas: "img content";
}
.media .image {
	grid-area: img;
}
.media .text {
	grid-area: content;
	padding: 10px;
}
```
``` html
<div class='media'>
	<div class='image'></div>
	<div class='text'>
	 lorem ipsum dolor sit amet
	</div>
</div>

```

##### grid definition shorthands
- These can quickly become difficult to read for other developers, or even your future self. However they are part of the specification and it is likely you will come across them in examples or in use by other developers, even if you choose not to use them.
###### `grid-template`
- the [`grid-template`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template) property sets the following properties:
	- [`grid-template-rows`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-rows)
   - [`grid-template-columns`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-columns)
   - [`grid-template-areas`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-areas)
- the property is referred to as the Explicit Grid Shorthand because it is setting those things that you control when you define an explicit grid, and not those which impact any implicit row or column tracks that might be created.
- The first value is our `grid-template-areas` value but we also declare the size of the row at the end of each row. This is what the `minmax(100px, auto)` is doing.
``` css
.wrapper {
	display: grid;
	grid-template: 
	"h h h h h h h h h" minmax(100px, auto)
	"s s s m m m m m m" minmax(100px, auto)
	"f f f f f f f f f" minmax(100px, auto)
	/ 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;

}
```