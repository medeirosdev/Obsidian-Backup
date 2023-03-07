tags: #css 


- Combinators combine other selectors in a way that gives them a uself relationship to each other and the location of content in the document
- **descendant combinator**
	- it combines two selectors such that elements matched by the second selector are selected if they have an ancestor element matching the first selector
	- `body article p` -> a paragraph inside a article that is inside a body 
	- `.box p` -> match only the `<p>` element which is inside an element with a class of `.box`
- **child combinator**
	- the child combinator (`>`) matches only thoses element matched by the second selector that are the direct children of elements matched by first
	- `article > p` -> match only paragraphs which are a direct child of a article element
	- `ul > li` -> math only `<li>` tags which are the the direct children of a `<ul>` tag
- **adjacent sibling combinator**
	- the adjacent sibling selector (`+`) matches only thoses elements matched by the second selector that are the next sibling element of the first selector ^9c56a6
	- `p + img` -> select all `<img>` elements that are immediately preceded by a `<p>` element
	- `h1 + p` -> matches only the paragraphs elements that are immediately preceded by a `<h1>` element
- **general sibling combinator**
	- use this combinator to select siblings of an element even if they are not directly adjacent
	- `p ~ img` -> it selects all `<img>` element that come anywhere after `<p>` element