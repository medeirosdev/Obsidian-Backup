tags: #css 
###### reference
- [CSS variables - FreeCodeCamp](https://www.youtube.com/watch?v=GF8aoDqebsQ)

### css variables
- **defining a variable in global scope**
``` css
:root 
{
	--red: #ff6f69;
	--beige: #ffeead;
	--yellow: #ffcc5c;
}
```

---

- **using a css variable**
``` css
body {
	color: var(--red);
	background: var(--beige);
}
 a 
{
	color: var(--red);
}
.item {
	background: var(--yellow);
}
```

---

- **overriding css variables**
- we can override some variables inside, for example, a html element context 
- this will affect all the elements which are related to the item, even if we didn't explictly set the variable for use for that particular item (remeber the [[Cascade and Inheritance]])
``` css
.item 
{
	--red: #ff8e69;
	backgrund: var(--yellow);
}
```

---

- **local variables**
- only the children inside the element can access the variable
``` css

#navbar 
{
	--nav-red: #ff6f19;
}
#navbar a 
{
	color: var(--nav-red);
}
```

---
- **creating themes with css variables**
- a good way to achieve this is by creating a new class and inside that class you just override the values for the variables declared previously
``` css
.purchased
{
	--red: #ff45eb;
	--button-color: #cc00ef;
	--border-radius: 10px;
}
```
---
- **changing variables with JavaScript**
``` css
:root 
{
	--red: #ff6f69;
	--beige: #ffeead;
	--yellow: #ffcc5c;
}
```


``` javascript
const root = document.querySelector(':root');
const rootStyle = getComputedStyle(root);
const red = rootStyles.getPropertyValue('--red'); // #ff6f69

rootStyle.setProperty('--red', 'green');

```