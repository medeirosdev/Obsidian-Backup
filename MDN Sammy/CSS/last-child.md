tags: #css 
- the `:last-child` _CSS pseudo-class_ represents the last element among a group of sibling elements
- the element will only be selected if it is the specified element by the selector and if it is the last element of a parent element
	- `p:last-child`

``` html
<div>
	<p>this text isn't selected</p>
	<p>this text is selected</p>
</div>
<div>
	<p>this text isn't selected</p>
	<h2>this text isn't selected: it's not a 'p'</h2>
</div>
```
``` css
p:last-child
{
	background-color:lime;
}
```