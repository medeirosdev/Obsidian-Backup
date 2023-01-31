# Add Rows with grid-template-rows
[[CSS]]
The grid you created in the last challenge will set the number of rows automatically. To adjust the rows manually, use the `grid-template-rows` property in the same way you used `grid-template-columns` in the previous challenge.

# Add Columns with grid-template-columns

Simply creating a grid element doesn't get you very far. You need to define the structure of the grid as well. To add some columns to the grid, use the `grid-template-columns` property on a grid container as demonstrated below:

```css
.container {
  display: grid;
  grid-template-columns: 50px 50px;
}
```

This will give your grid two columns that are each 50px wide. The number of parameters given to the `grid-template-columns` property indicates the number of columns in the grid, and the value of each parameter indicates the width of each column.

# Use CSS Grid units to Change the Size of Columns and Rows

You can use absolute and relative units like `px` and `em` in CSS Grid to define the size of rows and columns. You can use these as well:

`fr`: sets the column or row to a fraction of the available space,

`auto`: sets the column or row to the width or height of its content automatically,

`%`: adjusts the column or row to the percent width of its container.

Here's the code that generates the output in the preview:

```css
grid-template-columns: auto 50px 10% 2fr 1fr;
```

This snippet creates five columns. The first column is as wide as its content, the second column is 50px, the third column is 10% of its container, and for the last two columns; the remaining space is divided into three sections, two are allocated for the fourth column, and one for the fifth.

# Create a Column Gap Using grid-column-gap

So far in the grids you have created, the columns have all been tight up against each other. Sometimes you want a gap in between the columns. To add a gap between the columns, use the `grid-column-gap` property like this:

```css
grid-column-gap: 10px;
```

This creates 10px of empty space between all of our columns.

# Create a Row Gap using grid-row-gap

You can add a gap in between the rows of a grid using `grid-row-gap` in the same way that you added a gap in between columns in the previous challenge.

---

Create a gap for the rows that is `5px` tall.



# Add Gaps Faster with grid-gap

`grid-gap` is a shorthand property for `grid-row-gap` and `grid-column-gap` from the previous two challenges that's more convenient to use. If `grid-gap` has one value, it will create a gap between all rows and columns. However, if there are two values, it will use the first one to set the gap between the rows and the second value for the columns.

---

Use `grid-gap` to introduce a `10px` gap between the rows and `20px` gap between the columns.

# Use grid-row to Control Spacing

Of course, you can make items consume multiple rows just like you can with columns. You define the horizontal lines you want an item to start and stop at using the `grid-row` property on a grid item.

---

Make the element with the `item5` class consume the last two rows.


# Align an Item Horizontally using justify-self

In CSS Grid, the content of each item is located in a box which is referred to as a cell. You can align the content's position within its cell horizontally using the `justify-self` property on a grid item. By default, this property has a value of `stretch`, which will make the content fill the whole width of the cell. This CSS Grid property accepts other values as well:

`start`: aligns the content at the left of the cell,

`center`: aligns the content in the center of the cell,

`end`: aligns the content at the right of the cell.

---

Use the `justify-self` property to center the item with the class `item2`.

# Align All Items Horizontally using justify-items

Sometimes you want all the items in your CSS Grid to share the same alignment. You can use the previously learned properties and align them individually, or you can align them all at once horizontally by using `justify-items` on your grid container. This property can accept all the same values you learned about in the previous two challenges, the difference being that it will move **all** the items in our grid to the desired alignment.

# Divide the Grid Into an Area Template

You can group cells of your grid together into an area and give the area a custom name. Do this by using `grid-template-areas` on the container like this:

```css
grid-template-areas:
  "header header header"
  "advert content content"
  "advert footer footer";
```

The code above groups the cells of the grid into four areas; `header`, `advert`, `content`, and `footer`. Every word represents a cell and every pair of quotation marks represent a row.

# Place Items in Grid Areas Using the grid-area Property

After creating an area template for your grid container, as shown in the previous challenge, you can place an item in your custom area by referencing the name you gave it. To do this, you use the `grid-area` property on an item like this:

```css
.item1 {
  grid-area: header;
}
```

This lets the grid know that you want the `item1` class to go in the area named `header`. In this case, the item will use the entire top row because that whole row is named as the `header` area.


# Use grid-area Without Creating an Areas Template

The `grid-area` property you learned in the last challenge can be used in another way. If your grid doesn't have an areas template to reference, you can create an area on the fly for an item to be placed like this:

```css
item1 { grid-area: 1/1/2/4; }
```

This is using the line numbers you learned about earlier to define where the area for this item will be. The numbers in the example above represent these values:

```css
grid-area: horizontal line to start at / vertical line to start at / horizontal line to end at / vertical line to end at;
```

So the item in the example will consume the rows between lines 1 and 2, and the columns between lines 1 and 4.

# Reduce Repetition Using the repeat Function

When you used `grid-template-columns` and `grid-template-rows` to define the structure of a grid, you entered a value for each row or column you created.

Let's say you want a grid with 100 rows of the same height. It isn't very practical to insert 100 values individually. Fortunately, there's a better way - by using the `repeat` function to specify the number of times you want your column or row to be repeated, followed by a comma and the value you want to repeat.

Here's an example that would create the 100 row grid, each row at 50px tall.

```css
grid-template-rows: repeat(100, 50px);
```

You can also repeat multiple values with the repeat function and insert the function amongst other values when defining a grid structure. Here's what that looks like:

```css
grid-template-columns: repeat(2, 1fr 50px) 20px;
```

This translates to:

```css
grid-template-columns: 1fr 50px 1fr 50px 20px;
```

**Note:** The `1fr 50px` is repeated twice followed by 20px.

# Limit Item Size Using the minmax Function

There's another built-in function to use with `grid-template-columns` and `grid-template-rows` called `minmax`. It's used to limit the size of items when the grid container changes size. To do this you need to specify the acceptable size range for your item. Here is an example:

```css
grid-template-columns: 100px minmax(50px, 200px);
```

In the code above, `grid-template-columns` is set to create two columns; the first is 100px wide, and the second has the minimum width of 50px and the maximum width of 200px.

# Create Flexible Layouts Using auto-fill

The repeat function comes with an option called auto-fill. This allows you to automatically insert as many rows or columns of your desired size as possible depending on the size of the container. You can create flexible layouts when combining `auto-fill` with `minmax`, like this:

```css
repeat(auto-fill, minmax(60px, 1fr));
```

When the container changes size, this setup keeps inserting 60px columns and stretching them until it can insert another one. **Note:** If your container can't fit all your items on one row, it will move them down to a new one.

# Create Flexible Layouts Using auto-fit

`auto-fit` works almost identically to `auto-fill`. The only difference is that when the container's size exceeds the size of all the items combined, `auto-fill` keeps inserting empty rows or columns and pushes your items to the side, while `auto-fit` collapses those empty rows or columns and stretches your items to fit the size of the container.

**Note:** If your container can't fit all your items on one row, it will move them down to a new one.

