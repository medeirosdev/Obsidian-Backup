tags: #css , #status/unfinished 

[Reference material for cascade and inheritance](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance)


- **Cascade** is an algorithm that defines how user agents combine property values originating from different sources
	- The cascade defines the origin and layer that takes precedence when declarations is in more than one origin
- **Specificity** is the algorithm that the browser uses to decide which property value is applied to an element ^ed090c
- **Inheritance**: concept which means that some CSS properties by default inherit values set on the current element's parent element and some don't
###### Controlling Inheritance
- CSS provides five special universal property values for controlling inheritance.
	- `inherit`
		- sets the property value applied to a selected element to be the same as that of its parent element.
		- This turns on inheritance
	- `initial`
		- sets the property value applied to a selected element to the _initial value_ of that property
		- _initial value_: it sets the property value as listed in its definition table in the **_specification_**
		- it's like not having a value at all, not even the user-agent's stylesheet
	- `revert`
		- resets the property value applied to a selected element to the browser's default styling
	- `revert-layer`
		- resets the property value applied to a selected element to the value established in a previous _cascade layer_
	- `unset`
		- resets the property to its natural value, which means that if the property is naturally inherited it acts like `inherit`, otherwise it acts like `initial`
###### Resetting all property values
- The CSS shorthand property `all` can be used to apply one of these [[Cascade and Inheritance#Controlling Inheritance|inheritance properties]] to (almost) all properties at once
``` css
.special-class
{
	all:unset; /* all properties will be set to the formal definition values*/
}
```

###### Specificity

- The amount of specificity a selector has is measured using three different values which can bas thought of as _ID_, _CLASS_, and _ELEMENT_ columns in the hundreds, tens, and ones place
- **Identifiers**
	- score one in this column for each _ID_ selector contained inside the overall selector
- **Classes**
	- score on in this column for each _class_ selector, _attribute_ selector, or _pseudo-class_ contained inside the overall selector
- **Elements**
	- socre on in this column for each _element_ selector or _pseudo-element_ contained inside the overall selector

>[!caution]
>The universal selector (*), combinators(+, >, ~, ''), ans specificity adjustement selector (`:where()`) have no effect on specificity

- The negation (`:not()`) and the matches-any (`:is()`) pseudo-classes themselves don't have effect on specificity, but their parameter do
	- The specificity that each contributes to the specificity algorithm is the specificity of the selector in the parameter that has the greatest weight
- Specifity analysis example:
- ![specifity](https://i.imgur.com/44dIWoo.jpg)

###### !important

- This flag is used to make an individual property and value pair the most specific rule, thereby overriding the normal rules of the cascade, including normal inline styles.
``` css
.better {
    background-color: gray;
    border: none !important;
}
```