tags: #css 

- the `:where()` _pseudo-class_ function takes a selector list as its argument, and selects any element that can be selected by one of the selectors in that list
- the difference between `:where()` and [[is()]] is that `:where()` always has _0 specificity_, whereas `:is()` takes on the specificity of the most specific selectors in its arguments
###### example
``` css

:where(footer.someClass) a
{
	color: orange;
}
footer a 
{
	color: blue;
}
```
- the blue color will be applied because the `:where` specificity is always 0