tags: #css

- the `:is()` pseudo-class function takes a selector list as its argument, and selects any element that can be selected by one of the selectors in that list
``` css

:is(ol, ul) > :is(ol, ul)
{
	background-color: tomato;
	list-style-type: lower-greek;
}
```


>[!warning] :is() limitability
>the `:is()` pseudo-class does not match **pseudo-elements**


###### forgiving selector parsing
- in CSS when using a selector list, if any of the selectors are invalid then the whole list is deemed invalid
- when using `:is()` or `:where()` instead of the whole list of selectors being deemed invalid if one fails to parse, the incorrect or unsupported selector will be ignored and the other used

###### difference between `:is()` and `:where()`
- `:is()` counts towards the specificity of the overall selector (it takes the specificity of its most specific argument), whereas `:where()` has a specificity value of 0
###### simplifying list selectors
``` css

:is(ol, ul, menu, dir) :is(ol, ul, menu, dir) :is(ul, menu, dir)
{
	list-style-type: square;
}

/* Level 1 */
:is(section, article, aside, nav) h1
{
	font-size:25px;
}
/* Level 2 */

:is(section, article, aside, nav) :is(sectionm article, aside, nav) h1
{
	font-size: 20px;
}
/* level 3 */

:is(section, article, aside, nav)
:is(section, article, aside, nav)
:is(section, article, aside, nav)
{
	font-size:15px;
}
```
###### more examples
``` css
header:is(.main, .bright, .color)
{
	/*
		Match any header element whose class values could be .main, .bright or .color
	*/
}
header *:has(h1, h2)
{
	/*
		match any h1 or h2 element inside a header tag
	*/
}
:is(header, main) > h2
{
	/*
		match a h2 which is a directly children of either a header tag or a main tag
	*/
}
```