tags: #css 

- the `:first-of-type` _CSS pseudo-class_ represents the first element of its type among a group of **sibling** elements
- In contrast to the [[first-child]] _pseudo-class_ the element doesn't need to be the exactly first in order child of a parent element
``` html
<dl>
	<dt>Vegetables:</dt>
	<dd>1. tomatoes</dd>
	<dd>2. cucumbers</dd>
	<dd>3. mushrooms</dd>
	<dt>Fruits:</dt>
	<dd>4. apples</dd>
	<dd>5. mangos</dd>
	<dd>6. pears</dd>
	<dd>7. oranges</dd>
<dl>
```
``` css
dd:first-of-type
{
	border:2px solid orange;
}
```