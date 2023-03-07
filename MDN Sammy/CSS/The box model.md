tags: #css 

- In CSS we broadly have two types of boxes: **block** boxes and **inline** boxes

###### outer display type
- **if a box has an outer display type of `block`**
	- the box will break onto a new line
	- the `width` and `height` properties are respected
	- padding, margin and border will cause other elements to be pushed away from the box
	- the box will extend in the inline direction to fill the space available in its container
- **if a box has an outer display type of `inline`**
	- the box will not break onto a new line
	- the `width` and `height` properties will not apply
	- vertical padding, margins, and borders will apply but will not cause other inline boxes to move away from the box
	- horizontal padding, margins, and borders will apply and will cause other inline boxes to move away from the box
###### inner display type
- boxes also have an _inner_ display type, which dictates how elements inside that box are laid out
- by default, the elements inside a box are laid out in **normal flow** and behave as block or inline boxes
- `flex` and `grid` are examples of inner display types
###### parts of a box
- making up a block box in CSS we have:
	- **Content box** ^d373dd
		- the area where your content is displayed; size it using properties like `inline-size` and `block-size` or `width` and `height`
	- **Padding box**
		- the padding sits around the content as white space; size it using `padding` and related properties;
	- **Border box**
		- the border wraps the content and any padding; size it using `border` and related properties
	- **Margin box**
		- the margin is the outermost layer; wrapping the content, padding, and border as whitespace between this box and other elements; size it using `margin` and related properties

###### the standard CSS box model
- in the standard box model, if you give a box an `inline-size` and a `block-size` attributes, this defines the inline-size and block-size of the [[The box model#^d373dd|content box]] 
- any padding and border is then added to those dimensions to get the total size taken up by the box
- Example:
``` css
.box
{
	width: 350px;
	height: 150px;
	margin:10px;
	padding:25px;
	border:5px solid black;
}

```
- the _actual_ space taken up by the box will be 410px wide (350 + 25 + 25 + 5 + 5) and 210px high (150px + 25 + 25 + 5 + 5)

###### the alternative CSS box model
- In the alternative box model, the content area width is that width minus the width for the padding and border
- to use the alternative box model for all of your elements, set the `box-sizing` property on the `<html>` element and set all other elements to inherit that value
```css
html
{
	box-sizing:border-box;
}
*,
*::before,
*::after
{
	box-sizing:inherit;
}



```
###### margin collapsing
- two positive margin will combine to become one margin; Its size will be equal to the largest individual margin
- two negative margins will collapse and the smallest (furthest from zero) value will be used
- if one margin is negative, its value will be subtracted from the total
