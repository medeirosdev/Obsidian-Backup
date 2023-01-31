tags: #css 

- this pseudo-class represents a way of selecting a parent element or a previous sibling element with respect to a reference element by taking a relative selector list as an argument
- the `has()` pseudo-class takes on the [[Cascade and Inheritance#^ed090c|specificity]] of the most specific selector in its argument
``` css
/*
Selects an h1 heading with a paragraph element that immediately follows the h1 and applies the style to h1
*/
h1:has(+ p)
{
	margin-bottom:0;
}
```

###### examples
- with the [[Combinators#^9c56a6|adjacent sibling combinator]]
	- the `:has()` in the following example adjusts the spacing after `<h1>` heading if they are immediately followed by an `<h2>` heading
``` css
h1:has(+ h2)
{
	margin: 0 0 0.25rem 0;
}
```
---
- with the `:is()` pseudo-class
	- the first `:is()` pseudo-class is used to select any of the heading elements in the list
	- the second `:is()` pseudo-class is used to pass a list of adjacent sibling selectors as an argument to `:has()`
	- the `:has()` pseudo-class helps to select any `H1`, `H2`, or `H3` element that is immediately followed by an `H2`, `H3`, or `H4` element and the CSS rule reduces the spacing after such `H1`, `H2`, or `H3` elements.
###### logical operations
- the `:has()` relational selector can be used to check if one of the multiple features is true or if all the features are true
- `x:has(a, b)` will style `x` if descendant `a` **OR** `b` exists
- `x:has(a):has(b)` will style `x` if descendant `a` **AND** `b` exists
``` css
body:has(video, audio) {
/*
styles to apply if the content contains audio OR video
*/
}

body:has(video):has(audio)
{
/*
styles to apply if the content contain both audio AND video
*/
}

```


