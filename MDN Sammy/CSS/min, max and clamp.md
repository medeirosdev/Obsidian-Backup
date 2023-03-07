tags: #css 

- **reference**
	- [clamp](https://developer.mozilla.org/en-US/docs/Web/CSS/clamp)
	- [min](https://developer.mozilla.org/en-US/docs/Web/CSS/min)
	- [max](https://developer.mozilla.org/en-US/docs/Web/CSS/max)
---
###### min
- `min(value, value)` -> the function will analise the values and it will choose the smallest values between the two of them
- the code for `min()` is equivalent to the code below
``` css
.selector
{
	width: 70%;
	max-width: 600px;
	/* same result */
	width: min(70%, 600px);
}
```
###### max
- `max(value, value)` -> the function will choose the biggest value from the arguments
- this is equivalent to writing the code below
``` css
.selector
{
	width: 70%;
	min-width: 600px;
}
```

###### clamp
- `clamp(min, prefered, max)` 
``` css
.sec
{
	width: clamp(300px, 50%, 20rem);
}
```
- the code above: the ideal size for the `.sec` is 50% of its parent container, but its size must be at minumum 300px but the biggest it can get is 20rem
---
- `clamp()` is great for controlling the size of texts