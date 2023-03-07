tags: #css 

> [!warning] `auto`
> using animation with `auto` may lead to unpredictable results, depending on the browser and its version, and should be avoided

- `transition-property`
	- specifies the name or names of the CSS properties to which transitions should be applied
- `transition-duration`
	- specifies the duration over which transitions should occur
- `transition-timing-function`
	- specifies a function to define how intermediate values for properties are computed
- `transition-delay`
	- defines how longe to wait between the time a property is chanded and the transition begins
--- 
- the `transition` shorthand CSS syntax is written as follows
``` css
div 
{
	transition: <property> <duration> <timing-function> <delay>;
}
```
---
- multiple animated properties example
``` css
.box 
{
	transition: width 2s, height 2s, background-color 2s, transform 2s;
}
```
--- 
###### JavaScript examples
> [!warning]  Care should be taken when using a transition immediately after:
> - adding the element to the DOM using `.appendChild()`
> - removing an element's `display:none;` property

- this is treated as if the initial state had never occurred and the element was always in its final state. The easy way to overcome this limitation is to apply a `setTimeout()` of a handful of milliseconds before changing the CSS property you intend to transition to
``` javascript
const square = document.createElement('div');
square.classList.add('square');

setTimeout(()=>
{
    square.classList.add('active');
}, 1000)

document.body.appendChild(square);
```

###### detecting the start and completion of a transition
- you can use the `transitionend` event to detect that an animation has finished running
- you detect the beginning of a transition using `transitionrun` (fires before any delay) and `transitionstart` (fires after any delay)
