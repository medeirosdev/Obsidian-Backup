tags: #css 
##### backgrounds
- `background-repeat`
	- the `background-repeat` property is used to control the tiling behavior of images.
	- `no-repeat` -> stop the background from repeating altogether
	- `repeat-x` -> repeat horizontally
	- `repeat-y` -> repeat vertically
	- `repeat` -> the default; repeat in both directions
- `background-size`
	- `x-value, y-value` -> you can use any kind of value unit
	- `cover` -> the browser will make the image just large enough so that it completely covers the box area while retaining its aspect ratio. In this case, part of the image is likely to end up outside the box
	- `contain` -> the browser will make the image the right size to fit inside the box. In this case, you may end up with gaps on either side or oon the top and bottom of the image, if the aspect ratio of the image is different from that of the box
- `background-position`
	- syntax: `background-position: horizontal_value, vertical_value`
	- the default `background-position` value is (0, 0
	- you can use keywords such as `top` and `right` interchangeably in any position
	- you can also use a 4-value syntax in order to indicate a distance from certain edge of the box - the length unit, in this case, is an offset from the value that precedes it
		- In this case we are positioning the background 20px from the top and 10px from the right
		- `background-position: top 20px right 10px`;

###### gradient backgrounds
- it is set by using the `background-image` property
``` css
.a
{
	background-image:linear-gradient(105deg, rgba(0, 249, 255, 1) 39%, rgba(51, 56, 57, 1) 96%);
}
.b
{
	background-image: radial-gradient(circle, rgba(0, 249, 255, 1) 39%, rgba(51, 56, 57, 1) 96%);
}

```
###### multiple background images
- you can specify multiple `background-image` values in a single property value, separating each one with a comma
- the backgrounds will layer with the last list background image at the bottom of the stack, and each previous image stacking on top of the one that follows it in the code
``` css
background-image: url(image1.png), url(image2.png), url(image3.png), url(image4.png);
background-repeat: no-repeat, repeat-x, repeat;
background-position: 10px 20px, top right;
```
- what happens when different properties have different numbers of values?
	- the answer is that the smaller number of values will cycle


###### background attachment
- another option we have available for backgrounds is specifying how they scroll when the content scrolls
- more information on [this site about background attachment](https://mdn.github.io/learning-area/css/styling-boxes/backgrounds/background-attachment.html)
- this is controlled using the `background-attachment` property, which can take the following values
	- `scroll` -> default value; causes the element's background to scroll when the page is scrolled. If the element content is scrolled, the background does not move. In effect, the background is fixed to the same position on the page, so it scrolls as the page scrolls.
		- you can test it by setting on a parent the overflow property to `scroll` and making the child content overflow the parent container
	- `fixed` -> causes an element's background to be fixed to the viewport so that it doesn't scroll when the **page or element content is scrolled**. It will **always** remain in the same position on the screen.
	- `local` -> fixed the background to the element it is set on, so when you scroll the element the background scrolls with it
###### background short-hand property
- This shorthand lets you set all of the different properties at once
- if using multiple backgrounds, you need to specify all of the properties for the first background, then add your next background after a comma
- **rules**
	- a `background-color` may only be specified after the final comma
	- the value of `background-size` may only be included immediately after `background-position`, separated with the '/' character, like this: `center/80%`
``` css
.box
{
linear-gradient(105deg, rgba(255, 255, 255, .2) 39%, rgba(51, 56, 57, 1) 96%)
center center/ 400px 200px no-repeat, url(big-star.png) center no-repeat, rebeccapurple
}
```

##### borders
- We can set a border for all four sides of a box with `border`:
``` css
.box
{
	border:1px solid black;
}
```
- Or we can target one edge of the box, for example:
``` css
.box
{
	border-top:1px solid black;
}
```
- The individual properties for these shorthands
``` css
.box{
	border-top-width:1px;
	border-top-style:solid;
	border-top-color:black;
}
```
###### rounded corners
- rounding corners on a box is achieved by using the `border-radius` property and associated longhands which relate to each corner of the box
- two lengths or percentages may be used as a value, the **first** value defining the **horizontal** radius, and the second the vertical radius

- Making the top right corner have a horizontal radius of 1em and a vertical radius of 10%
``` css
.box{
	border-top-right-radius:1em 10%;
}
```