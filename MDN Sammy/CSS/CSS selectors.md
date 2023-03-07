tags: #css 

- [[Type, class and ID selectors]]
- [[Attribute selectors]]
- [[Pseudo-classes and pseudo-elements]]
- [[Combinators]]



###### selector lists
- if you have more than one thing which uses the same CSS then the individual selectors can be combined into a selector list so that the rule is applied to all of the individual selectors

``` css
h1, 
.special
{
	color:blue;
}
```

>[!caution]
>When you group selectors in this way, if any selector is syntactically invalid, the whole rule **will be ignored**


###### attribute selectors

- this group of selectors gives you different ways to select elements based on the presence of a certain attribute on an element
``` css
a[title] {}
a[href='https://example.com']{}


```

###### pseudo-classes and pseudo-elements
- this group of selectors includes pseudo-classes, which styles certain states of an element. The `:hover` pseudo-class, for example, selects an element only when it is being hovered over by the mouse pointer
- it also includes pseudo-elements, which select a certain part of an element rather than the element itself. `::first-line` always selects the first line of text inside an element
``` css
a:hover{}
p::first-line{}


```
###### combinators
- This selectors combine other selectors in order to target elements within our documents
``` css
article > p
{}
```