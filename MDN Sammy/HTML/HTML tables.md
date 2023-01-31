tags: #html

##### allowing cells to span multiple rows
- use `colspan` to span multiple columns
- use `rowspan` to span multiple rows
``` html
		<table>
	          <tr>
	            <th colspan="2">Animals</th>
	          </tr>
	          <tr>
	            <th colspan="2">Hippopotamus</th>
	          </tr>
	          <tr>
	            <th rowspan="2">Horse</th>
	            <td>Mare</td>
	          </tr>
	          <tr>
	            <td>Stallion</td>
	          </tr>
	          <tr>
	            <th colspan="2">Crocodile</th>
	          </tr>
	          <tr>
	            <th rowspan="2">Chicken</th>
	            <td>Hen</td>
	          </tr>
	          <tr>
	            <td>Rooster</td>
	          </tr>
       </table>
```


##### providing common stylying to columns
- HTML has a method of defining styling information for an entire column of data all in one place - the `<col>` and `<colgroup>` elements
- `<col>` elements are specified inside a `<colgroup>` container just below the opening `<table>` tag
- If we wanted to apply the styling information to both columns, we could just include one `<col>` element with a span attribute on it, like this: `<col style='color:red;' span=2>`
``` html
<table>
	<colgroup>
	<col/> <!-- skipping the first column-->
	<col style='background-color:yellow'>

	</colgroup>
	<tr>
		<th>Data 1</th>
		<th>Data 2</th>
	</tr>
	<tr>
		<td>Calcutta</td>
		<td>Orange</td>
	</tr>
	<tr>
		<td>Robots</td>
		<td>Jazz</td>
	</tr>
</table>
```
##### advanced features and accessibility

###### the `scope` attribute
- The `scope` attribute can be added to the `<th>` element to tell screen readers exactly what cells the header is a header for - is it a header for the row it is in, or the column -
- `scope` has two more possible values - `colgroup` and `rowgroup`
	- These are used for headings that sit over the top of multiple columns or rows
``` html
<thead>
	<!--- column scope -->
	<tr>
		<th scope="col">Purchase</th>
		<th scope="col">Location</th>
		<th scope="col">Evaluation</th>
		<th scope="col">Cost</th>
	</tr>
</thead>
```

``` html
<tr>
	<!-- row scope -->
	<th scope='row'>Haircut</th>
	<td>Hairdresser</td>
	<td>12:09</td>
	<td>Great ideia</td>
	<td>30</td>
</tr>

```
###### the `id` and `headers` attributes
- `id`
	- You add a unique `id` to each `<th>` element
- `headers`
	- You add a `headers` attribute to each `<td>` element
	- Each `headers` attribute has to contain a list of the `id`s of all the `<th>` elements that act as a header for that cell, separated by spaces

Use of the aforementioned attributes:

[Full fledged example using the header and id attributes](https://github.com/mdn/learning-area/blob/main/html/tables/advanced/items-sold-headers.html)

``` html
...
<thead>
	<tr>
		<th id='purchase'>Purchase</th>
		<th id='location'>Location</th>
		<th id='date'>Date</th>
		<th id='evaluation'>Evaluation</th>
		<th id='cost'>Cost </th>
	</tr>
</thead>
<tbody>
	<tr>
		<th id='haircut'>Haircut</th>
		<td headers='location haircut'>Haidresser</td>
		<td headers='date haircut'>12/09</td>
		<td headers='evaluation haircut'>Great ideia</td>
		<td headers='cost haircut'>30</td>

	</tr>

</tbody>

....
```