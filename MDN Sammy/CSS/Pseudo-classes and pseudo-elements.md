tags: #css 

###### pseudo-class
- a pseudo-class is a selector that selects elements that are in a specific state, e.g. they are the first element of their type, or they are being hovered over by the mouse pointer ^3bb6e2
``` css
article p:first-child
{} /* selects the p element when there is a p tag that is the first child element of a article parent element */
```
- Other examples of pseudo-class: `:last-child`, `:only-child`, `:invalid`
- **user-action pseudo classes**
	- user-action pseudo classes are classes that are applied only when the user interacts with the document in some way
	- `:hover`, `:focus` are good examples
###### pseudo-element
- pseudo-elements acts as if you had added a whole new HTML element into the markup
- pseudo-elements, **generally**, starts with a double colon `::`
``` css
article p::first-line {
    font-size: 120%;
    font-weight: bold;
}
/* ::first-line a pseudo-element which only selects the first line of a paragraph */
```