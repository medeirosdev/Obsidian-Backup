tags: #css 
- Overflow is what happens when there is too much content to fit in a container

###### the overflow property
- the `overflow` property is how you take control of an element's overflow
- the default value of `overflow` is `visible`
- To crop content when it overflows, you can set `overflow:hidden`
- Using `overflow: scroll`, browsers with visible scrollbars will always display them—even if there is not enough content to overflow
- If you only want scrollbars to appear when there is more content than can fit in the box, use `overflow: auto`. This allows the browser to determine if it should display scrollbars.
> [!note]
> You can specify `x` and `y` scrolling using the `overflow` property, passing two values. If two keywords are specified, the first applies to `overflow-x` and the second applies to `overflow-y`. Otherwise, both `overflow-x` and `overflow-y` are set to the same value