tags: #css 

- **Type selectors**
	- a _type selector_ is sometimes referred to as a _tag name selector_ or _element selector_ because it selects an HTML tag/element in your document
- **The universal selector**
	- the universal selector is indicated by an asterisk `*`
	- it selects everything in the document (or inside the parent element if it is being chained together with another element and a descendant combinator)
- **Class selectors**
	- the class selector starts with a dot (`.`) character
	- you can create a selector that will target specific elements with the class applied
		- `span.hightlight` -> it will select any `span` with a class of `highlight`
	- you can also create a selector which will match only if a element contains multiple classes applied to it 
		- `.highlight.danger.warning` -> it will select only element which have these three classes applied to it
- **ID selectors**
	- an _ID_ selector begins with a `#` rather than a dot character, but it used in the same way as a class selector
	- an _ID_ can be used only once per page, and elements can only have a single _ID_ value applied to them
