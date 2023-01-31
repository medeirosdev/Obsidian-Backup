## The HTML DOM NodeList Object
[[JS]]
A `NodeList` object is a list (collection) of nodes extracted from a document.

A `NodeList` object is almost the same as an `HTMLCollection` object.

Some (older) browsers return a NodeList object instead of an HTMLCollection for methods like `getElementsByClassName()`.

All browsers return a NodeList object for the property `childNodes`. 

Most browsers return a NodeList object for the method `querySelectorAll()`.

The following code selects all `<p>` nodes in a document:

### Example

const myNodeList = document.querySelectorAll("p");

The elements in the NodeList can be accessed by an index number.

To access the second <p> node you can write:

myNodeList[1]

**Note:** The index starts at 0.

---

## HTML DOM Node List Length

The `length` property defines the number of nodes in a node list:

### Example

myNodelist.length

The `length` property is useful when you want to loop through the nodes in a node list:

### Example

Change the color of all <p> elements in a node list:

const myNodelist = document.querySelectorAll("p");  
for (let i = 0; i < myNodelist.length; i++) {  
  myNodelist[i].style.color = "red";  
}

## The Difference Between an HTMLCollection and a NodeList

A **NodeList** and an **HTMLcollection** is very much the same thing.

Both are array-like collections (lists) of nodes (elements) extracted from a document. The nodes can be accessed by index numbers. The index starts at 0.

Both have a **length** property that returns the number of elements in the list (collection).

An HTMLCollection is a collection of **document elements**.

A NodeList is a collection of **document nodes** (element nodes, attribute nodes, and text nodes).

HTMLCollection items can be accessed by their name, id, or index number.

NodeList items can only be accessed by their index number.

An HTMLCollection is always a **live** collection. Example: If you add a <li> element to a list in the DOM, the list in the HTMLCollection will also change.

A NodeList is most often a **static** collection. Example: If you add a <li> element to a list in the DOM, the list in NodeList will not change.

The `getElementsByClassName()` and `getElementsByTagName()` methods return a live HTMLCollection.

The `querySelectorAll()` method returns a static NodeList.

The `childNodes` property returns a live NodeList.

---

## Not an Array!

A NodeList may look like an array, but it is not.

You can loop through a NodeList and refer to its nodes by index.

But, you cannot use Array methods like push(), pop(), or join() on a NodeList.