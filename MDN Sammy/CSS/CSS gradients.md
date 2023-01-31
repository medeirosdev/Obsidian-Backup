tags: #css 
###### basic linear gradient
- all you need is to specify two or more colors. These are called _color stops_
	- the order of the colors makes difference on the output
- `background: linear-gradient(blue, pink)`
- linear gradients run from top to bottom
###### diagonal gradient
- you can even make the gradient run diagonally
``` css
.diag
{
	background: linear-gradient(to bottom right, blue, pink);
}
```
###### using angles
- you can give the gradient a specific angle
``` css
.angled
{
	background: linear-gradient(70deg, blue, pink)
}
```
- when using an angle, `0deg` creates a vertical gradient running bottom to top
- `90deg` creates a horizontal gradient running left to right, and so on in a clockwise direction
- **negative angles run in the counterclockwise direction**
##### declaring color and creating effects
###### positioning color stops
- you can give each color stop a value in percentage or a absolute value
- `0%` represents the starting point, while `100%` represents the ending point
- If you leave a location unspecified, the position of that particular color stop will be automatically calculated for you, with the first color stop being at `0%` and the last color stop being at `100%`, and any other color stops being half way between their adjacent color stops
###### creating hard lines
- adjacent color stops can be set to the same location
``` css
.striped{
	background: linear-gradient(180deg, cyan 50%, palegoldenrod 50%);
}
```

###### gradient hints
- by default, the gradient transitions evenly from one color to the next
- you can include a color-hint to move the midpoint of the transition value to a certain point along the gradient
``` css
.color-hint {
	background: linear-gradient(blue, 10%, pink);
}
```
###### creating color band and stripes
- to include a solid, non-transitioning color area within a gradient, include two positions for the color stop
``` css

.grad
{
	background: linear-gradient(
		to left,
		lime 25%,
		red 25% 50%,
		cyan 50% 75%,
		yellow 75%
			
	)
}
```
###### overlaying gradients
- the backgrounds are stacked from top to bottom, with the first specified being on top
``` css
.div {
	background: linear-gradient(to right, transparent, mistyrose),
	url('backgroundImage.png');
}
```
- you can even strack gradients with other gradients. As long as the top gradients aren't opaque, the gradients below will still be visible.




##### using radial gradients
