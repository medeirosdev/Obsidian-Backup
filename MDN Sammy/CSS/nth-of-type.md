tags: #css 
- the `:nth-of-type` _CSS pseudo-class_ matches elements based on their position among a sibling of the same type
``` html
<dl>
	<dt>vegetables:</dt>
	<dd>1. tomatoes</dd>
	<dd>2. cucumbers</dd>
	<dd>3. mushrooms</dd>
	<dt>fruits:</dt>
	<dd>4. apples</dd>
	<dd>5. mangos</dd>
	<dd>6. pears</dd>
	<dd>7. oranges</dd>
</dl>
```
----
``` html
 <div>
        <div>this element isn't counted</div>
        <p>1st paragraph</p>
        <p>2nd paragraph</p>
        <div>this element isn't counted</div>
        <p>3rd paragraph</p>
        <p>4th paragraph</p>
        <p>5th paragraph</p>
     </div>
```
``` css
p:nth-of-type(2n + 1)
{
	background: lime;
}
```