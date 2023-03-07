tags: #css 

- the `:first-child` _CSS pseudo-class_ represents the first element among a group of sibling elements
- it selects just the **FIRST CHILD** of a parent element, you can specify the type of the element that you want by adding the element just before the selector `p:first-child`

``` html
<div>
	<p>this text will be selected</p>
	<p>this text will not be selected</p>
<div>

<div>
	<h2>this will not be selected</h2>
	<p>this also will not be selected</h2>
</div>
```
``` css
p:first-child
{
	background-color:green;
}
```
- the next example will be a code to always select the first `li` within a `ul` even if it is a nested element
``` css

ul li:first-child
{
	background-color: blue;
}
```