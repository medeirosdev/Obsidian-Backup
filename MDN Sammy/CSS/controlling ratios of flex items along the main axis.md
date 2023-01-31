tags: #css

##### important concepts when working on the main axis
###### flex item sizing
- there is a concept in CSS of `min-content` and `max-content`
- the first paragraph has a width of `min-content`
	- the text has taken all of the soft wrapping opportunities available to it, becoming as small as it can be without overflowing
	- the longest word in the string is dictating the size

<div style='width:min-content; outline:3px dotted blue; margin:20px auto;'> Lorem ipsum dolor sit amet consectetur adipisicing elit. Ratione architecto rerum quas deleniti libero autem voluptatibus</div>

- the second paragraph has a value of `max-content` and so it does the opposite
	- it gets as big as it possible can be, taking no soft-wrapping opportunities


<div style='outline:3px dotted grey;'>
<p style='width:max-content;'>I am sized with max-content and so I will take none of the soft-wrapping opportunities.</p>
</div>

###### positive and negative free space
- When a flex container has positive free space, it has more space than is required to display the flex items inside the container
- We have negative free space when the natural size of the items adds up to larger than the available space in the flex container
###### flex-basis property
- the `flex-basis` property specified the initial size of the flex item before any space distribution happens
- the initial value for this property is `auto`
- in a `flex-direction: column`, the `flex-basis` will be equivalent to the height
- If `flex-basis` is set to `auto` then to work out the initial size of the item the browser first checks if the main size of the item has an absolute size set.
	- This would be the case if you had given your item a width of 200 pixels. In that case `200px` would be the `flex-basis` for this item.
	- If your item is instead auto-sized, then `auto` resolves to the size of its content
###### combining flex-grow and flex-basis
- `flex:1 1 auto`
	- in this case the `flex-basis` value is auto and the items don't have a width set, and so are auto-sized
	- this means that flexbox is looking at the `max-content` size of the items
- if we want equally-sized items, even if they start out at different sizes, you should use this
- `flex: 1 1 0`

