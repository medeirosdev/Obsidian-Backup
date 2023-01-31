## The HTMLCollection Object

The `getElementsByTagName()` method returns an `HTMLCollection` object.

An `HTMLCollection` object is an array-like list (collection) of HTML elements.

The following code selects all `<p>` elements in a document:

### Example

const myCollection = document.getElementsByTagName("p");

The elements in the collection can be accessed by an index number.

To access the second <p> element you can write:

myCollection[1]

**Note:** The index starts at 0.

---

## HTML HTMLCollection Length

The `length` property defines the number of elements in an `HTMLCollection`:

### Example

myCollection.length

The `length` property is useful when you want to loop through the elements in a collection:

### Example

Change the text color of all <p> elements:

const myCollection = document.getElementsByTagName("p");  
for (let i = 0; i < myCollection.length; i++) {  
  myCollection[i].style.color = "red";  
}

**An HTMLCollection is NOT an array!**  

An HTMLCollection may look like an array, but it is not.

You can loop through the list and refer to the elements with a number (just like an array).

However, you cannot use array methods like valueOf(), pop(), push(), or join() on an HTMLCollection.