tags: #css 

- the `:not()` _pseudo-class_ represents elements that do not match a list of selectors
``` css

p:not(.irrelevant)
{
	font-weight: bold;
	/*
	It will match any p that does not contain the irrelevant class
	*/
}
```

###### description
- there are several unusual effects and outcomes when using `:not` that you should keep in mind when using it
---

- this pseudo-class can increase the specificity of a rule. for example, `#foo:not(#bar)` will match the same element as the simpler `#foo`, but has the higher specificity of two `id` selectors
---

- The specificity of the `:not()` pseudo-class is replaced by the specificity of the most specific selector in its comma-separated argument of selectors; providing the same specificity as if it had been written `:not(:is(argument))`
---

- `:not(.foo)` will match anything that isn't `.foo`, including `<html>` and `<body>`
---

- You can negate several selectors at the same time. Example: `:not(.foo, .bar)` is equivalent to `:not(.foo):not(.bar)`.
---

- This selector will match everything that is "not an X". This may be surprising when used with [descendant combinators](https://developer.mozilla.org/en-US/docs/Web/CSS/Descendant_combinator), since there are multiple paths to select a target element. For instance, `body :not(table) a` will still apply to links inside a `<table>`, since `<tr>`, `<tbody>`, `<th>`, `<td>`, `<caption>`, etc. can all match the `:not(table)` part of the selector
---

- if any selector passed to the `:not()` is invalid or not supported by the browser, the **whole rule will be invalidated**
	- the effective way to overcome this behavior is to use `:is` pseudo-class
	- `:is(:not(.foo), :not(:invalid-pseudo-class))`
###### examples
``` css
/*
<p> elements that don't have a class '.fancy'
*/
p:not(.fancy){}

/*
elements that are not <p> elements
*/
body :not(p){}

/*
Elements that are not <div> and not <span> elements
*/
body :not(div):not(span){}

/* elements that are not <div> or '.fancy' */

body :not(div, .fancy){}


```