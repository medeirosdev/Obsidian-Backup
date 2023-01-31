tags: #css 
- the flexible box module was designed as a one-dimensional layout model

##### the two axes of flexbox
- there's two axes -> **main axis** and the **cross axis**
- the **main axis** the defind by the `flex-direction` property and the **cross axis** runs perpendicular to it
###### main axis
- the main axis is defined by `flex-direction`, which has four possible values
	- `row`
	- `row-reverse`
	- `column`
	- `column-reverse`
- should you choose `row` or `row-reverse`, your main axis will run along in the `inline direction`
![main axis](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox/basics1.png)
- choose `column` or `column-reverse` and your main axis will run from the top of the page to the bottom - in the `block direction`
![main axis column direction](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox/basics2.png)

###### cross axis
- the **cross axis** runs perpendicular to the **main axis**
![cross axis](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox/basics3.png)
- if your main axis is `column/column-reverse` then the cross axis runs along the rows
![cross axis](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox/basics4.png)


##### the flex container
- an area of a document laid out using flexbox is called a **flex container**
- when creating a flex container all of the contained flex items will behave in the following way
	- `flex-direction:row`
	- the items do not stretch on the main dimension, bu can shrink
	- the items will stretch to fill the size of the cross axis
	- `flex-basis: auto`
	- `flex-wrap: nowrap
- the result of this is that your items will all line up in a **row**, using the **the size of the content as their size in the main axis**. if some items are taller than other, **all items will stretch along the cross axis to fill its full size**

###### changing flex-direction
- setting `flex-direction:row-reverse` will keep the items displaying along the row, however the start and end lines are switched
- if we try `flex-direction:column`, the main axis switches and our items now display in a column
	- set `column-reverse` and the start end end lines are again switched
##### flex-flow shortand
- you can combine the two properties `flex-direction` and `flex-wrap` into the `flex-flow` shorthand
- `flex-flow: row wrap`;
##### properties applied to flex items
- **flex item properties**
	- `flex-grow`
	- `flex-shrink`
	- `flex-basis`
- What we are doing when we change the value of these flex properties is to change the way that the available space is distributed amongst our items
###### flex-basis property
- the `flex-basis` property is what defines the size of that item in terms of the space it leaves as available space
- the initial value of this property is `auto` - in this case the browser looks to see if the items have a size.
- it the items don't have a size then the content's size is used as the `flex-basis`
	- This is why when we just declare `display: flex` on the parent to create flex items, the items all move into a row and take only as much space as they need to display their contents.
###### flex-grow property
- this property will cause the item stretch and take up any available space on that axis, or a proportion of the available space
###### flex-shrink property
- If we do not have enough space in the container to lay out our items, and `flex-shrink` is set to a positive integer, then the item can become smaller than the `flex-basis`
- the minimum size of the item will be taken into account while working out the actual amount of shrinkage that will happen
###### flex property
- predefined values for the `flex` property are as follows:
	- `flex:initial`
	- `flex:auto`
	- `flex:none`
	- `flex: <positive-number>`
- setting `flex:initial` resets the item to the initial values of flexbox
	- this is the same as `flex: 0 1 auto`
- using `flex: auto` is the same as using `flex: 1 1 auto`
- everything is as with `flex:initial` but in this case the items can't grow and fill the container as well as shrink if required.
- using `flex:none` will crate fully inflexible flex items. it is as if you wrote `flex: 0 0 auto`;
- `flex: 1` or `flex:1` is as if you use `flex: 1 1 0` or `flex: 2 1 0`
##### alignment, justification and distribution of free space between lines
###### align-items
- the `align-items` property will align the items on the cross axis
- the initial value for this property is `stretch`
###### justify-content
- the `justify-content` property is used to align the items on the main axis