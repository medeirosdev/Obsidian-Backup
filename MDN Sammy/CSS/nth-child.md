tags: #css 
- the `:nth-child()` _CSS pseudo-class_ matches elements based on their position among a group of siblings
- in the `element:nth-child()` syntax, the child count includes children of any element type; but it is considered a match only if the element at that child position is of the specified element type
``` html
<p>NBA players with most championships:</p>
<ul>
    <li>Bill Russell</li>
    <li>Sam Jones</li>
    <li>Tom Heinsohn</li>
    <li>K. C. Jones</li>
    <li>Satch Sanders</li>
    <li>John Havlicek</li>
    <li>Jim Loscutoff</li>
    <li>Frank Ramsey</li>
    <li>Robert Horry</li>
</ul>
```
``` css
li:nth-child(-n + 3) /* it will only select up to the third element*/ 
{
	border:2px solid orange;
	margin-bottom:1px;
}
li:nth-child(even)
{
	background-color: lightyellow;
}
```

###### examples
- `:nth-child(odd)` or `:nth-child(2n +1)`
	- represents the odd position elements
- `:nth-child(even)` or `:nth-child(2n)`
	- represents the even position elements
- `:nth-child(7)`
	- represents the seventh element
- `:nth-child(5n)`
	- represents the elements whose positions are a multiple of 5, including 0
- `:nth-child(n + 7)`
	- represents the seventh and all following elements
- `:nth-child(-n + 3)`
	- represents the first three elements
- `p:nth-child(n+8):nth-child(-n+15)`
	- represents the eighth through the fifteenth `<p>` elements of a group of siblings

###### the count
``` html
<div>
	<div>this element is counted</div>
	<p>1st paragraph and 2nd element</p>
	<p>2nd paragraph and 3rd element</p>
	<div>this element is counted and 4th element</div>
	<p>3rd paragraph and 5th element</p>
	<p>4th paragraph and 6th element</p>
	<p>5th paragraph and 7th element</p>
 </div>
```
``` css

p:nth-child(2n + 1)
{
	background-color: lime;
}
```
