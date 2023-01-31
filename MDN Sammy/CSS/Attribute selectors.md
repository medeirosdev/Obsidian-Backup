tags: #css 

###### presence and value selectors
- These selectors enable the selection of an element based on the presence of an attribute alone (for example `href`), or on various different matches against the value of the attribute
- `[attr]`
	- Matches elements with an `attr` attribute (whose name is the value in the square brackets)
	- `a[title]`
- `[attr=value]`
	- Matches elements with an `attr` attribute whose value is exactly `value`
	- `a[href="https://example.com"]`
- `[attr~=value]`
	- Matches elements with an `attr` attribute whose value is exactly `value`, or contains `value` in its (space separated) list of values
	- `p[class~="special"]`
- `[attr|=value]`
	- Matches elements with an `attr` whose value is exactly `value` or begins with `value` immediately followed by a hyphen


###### substring matching selectors
- these selectors allow for more advanced matching of substrings inside the value of your attribute
- If you want to match attribute values case-insensitively you can use the value `i` before the closing bracket
- `[attr^=value]`
	- Matches elements with an `attr` attribute, whose value begins with `value`
	- `li[class^="box-"]`
- `[attr$=value]`
	- Matches elements with an `attr` attribute whose value ends with `value`
	- `li[class$="-box"]`
- `[attr*=value]`
	- Matches elements with an `attr` attribute whose value contains `value` anywhere within the string
	- `li[class*="box"]`
