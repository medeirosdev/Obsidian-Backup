## Creating New HTML Elements (Nodes)

To add a new element to the HTML DOM, you must create the element (element node) first, and then append it to an existing element.

###  Example
[[JS]]
<div id="div1">  
  <p id="p1">This is a paragraph.</p>  
  <p id="p2">This is another paragraph.</p>  
</div>  
  
<script>  
const para = document.createElement("p");  
const node = document.createTextNode("This is new.");  
para.appendChild(node);  
  
const element = document.getElementById("div1");  
element.appendChild(para);  
</script>

---

## Example Explained 

This code creates a new `<p>` element:

const para = document.createElement("p");

To add text to the `<p>` element, you must create a text node first. This code creates a text node:

const node = document.createTextNode("This is a new paragraph.");

Then you must append the text node to the `<p>` element:

para.appendChild(node);

Finally you must append the new element to an existing element.

This code finds an existing element:

const element = document.getElementById("div1");

This code appends the new element to the existing element:

element.appendChild(para);

---

## Creating new HTML Elements - insertBefore()

The `appendChild()` method in the previous example, appended the new element as the last child of the parent.

If you don't want that you can use the `insertBefore()` method:

### Example

<div id="div1">  
  <p id="p1">This is a paragraph.</p>  
  <p id="p2">This is another paragraph.</p>  
</div>  
  
<script>  
const para = document.createElement("p");  
const node = document.createTextNode("This is new.");  
para.appendChild(node);  
  
const element = document.getElementById("div1");  
const child = document.getElementById("p1");  
element.insertBefore(para, child);  
</script>

---

## Removing Existing HTML Elements

To remove an HTML element, use the `remove()` method:

### Example

<div>  
  <p id="p1">This is a paragraph.</p>  
  <p id="p2">This is another paragraph.</p>  
</div>  
  
<script>  
const elmnt = document.getElementById("p1"); elmnt.remove();  
</script>

## Example Explained 

The HTML document contains a `<div>` element with two child nodes (two `<p>` elements):

<div>  
  <p id="p1">This is a paragraph.</p>  
  <p id="p2">This is another paragraph.</p>  
</div>

Find the element you want to remove:

const elmnt = document.getElementById("p1");

Then execute the remove() method on that element:

elmnt.remove();

The `remove()` method does not work in older browsers, see the example below on how to use `removeChild()` instead.

---

## Removing a Child Node

For browsers that does not support the `remove()` method, you have to find the parent node to remove an element:

### Example

<div id="div1">  
  <p id="p1">This is a paragraph.</p>  
  <p id="p2">This is another paragraph.</p>  
</div>  
  
<script>  
const parent = document.getElementById("div1");  
const child = document.getElementById("p1");  
parent.removeChild(child);  
</script>

---

## Example Explained 

This HTML document contains a `<div>` element with two child nodes (two `<p>` elements):

<div id="div1">  
  <p id="p1">This is a paragraph.</p>  
  <p id="p2">This is another paragraph.</p>  
</div>

Find the element with `id="div1"`:

const parent = document.getElementById("div1");

Find the `<p>` element with `id="p1"`:

const child = document.getElementById("p1");

Remove the child from the parent:

parent.removeChild(child);

Here is a common workaround: Find the child you want to remove, and use its `parentNode` property to find the parent:

const child = document.getElementById("p1");  
child.parentNode.removeChild(child);

---

## Replacing HTML Elements 

To replace an element to the HTML DOM, use the `replaceChild()` method:

### Example

<div id="div1">  
  <p id="p1">This is a paragraph.</p>  
  <p id="p2">This is another paragraph.</p>  
</div>  
  
<script>  
const para = document.createElement("p");  
const node = document.createTextNode("This is new.");  
para.appendChild(node);  
  
const parent = document.getElementById("div1");  
const child = document.getElementById("p1");  
parent.replaceChild(para, child);  
</script>