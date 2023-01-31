tags: #css

###### sizing images
- When using `object-fit` the replaced element can be sized to fit a box in a variety of ways
- `object-fit:cover` -> sizes the image down, maintaining the aspect ratio so that it neatly fills the box. As the aspect ratio is maintained, some parts of the image will be cropped by the box
- `object-fit:contain` -> the image will be scaled down until it is small enough to fit insde the box
- `object-fit:fill` -> it will fill the box but not maintain the aspect ratio
###### inheritance and form elements
- in some browsers, form elements do not inherit font styling by default
- You should add this rule to your CSS
``` css
button,
input,
select,
textarea
{
	font-family:inherit;
	font-size:100%;
	box-sizing:border-box;
	padding:0;
	margin:0;
}
textarea
{
	overflow:auto;
}
```