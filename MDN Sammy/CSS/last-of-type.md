tags: #css 

- the `:last-of-type` _CSS pseudo-class_ represents the last element of its type among a group of sibling elements
``` html
<article>
<p> this will not be selected </p>
<div>
	<p>first paragraph</p>
	<p>this will be selected</p>
</div>
<div>
	<p>the entire div will be selected</p>
	<p> test </p>
	<p>this will be selected</p>
</div>
<p> this will be the selected paragraph</p>
</article>
```
``` css
article *:last-of-type
{
	background: green;
}
```