tags: #css 
- In recent years, CSS has evolved in order to better support different directionality of content, including right-to-left but also top-to-bottom content.
- These different directionalities are called **writing modes**
	- a writing mode in CSS refers to whether the text is running horizontally or vertically

<h6 style='writing-mode:vertical-rl; background-color:red;text-align:center;'> Example</h6>


```css
h6
{
	writing-mode:vertical-rl;
}
```

- The three possible values for the `writing-mode` property are:
	- `horizontal-tb` -> top-to-bottom block flow direction. Sentences run horizontally
	- `vertical-rl` -> right-to-left block flow direction. Sentences run vertically
	- `vertical-lr` -> left-to-right block flow direction. Sentences run vertically
###### writing modes and block and inline layout
- block and inline is tied to the writing mode of the document, and not the physical screen
- when we switch the writing mode, we are changing which direction is block and which is inline
	- In a `horizontal-tb` writing mode the block direction runs from top to bottom
	- in a `vertical-rl` writing mode the block direction runs right-to-left horizontally
- Horizontal writing mode
	- ![horizontal writing mode](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Handling_different_text_directions/horizontal-tb.png)
- Vertical writing mode
	- ![Vertical writing mode](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Handling_different_text_directions/vertical.png)
###### logical properties and values
- The property mapped to `width` when in a horizontal writing mode is called `inline-size` 
- The property for `height` is named `block-size` 
``` css
.box
{
	inline-size:150px;
}
.horizontal
{
	writing-mode:horizontal-tb;
}
.vertical
{
	writing-mode:vertical-rl;
}
```
###### logical margin, border, and padding properties
- `margin-top` -> `margin-block-start`
- `padding-left` -> `padding-inline-start`
- `border-bottom` -> `border-block-end`