[[JS]]Iterables are iterable objects (like Arrays).

Iterables can be accessed with simple and efficient code.

Iterables can be iterated over with `for..of` loops

## The For Of Loop

The JavaScript `for..of` statement loops through the elements of an iterable object.

### Syntax

for (variable of iterable) {  
  // _code block to be executed_  
}  

---

## Iterating

Iterating is easy to understand.

It simply means looping over a sequence of elements.

Here are some easy examples:

-   Iterating over a String
-   Iterating over an Array

---

## Iterating Over a String

You can use a `for..of` loop to iterate over the elements of a string:

### Example

const name = "W3Schools";  
  
for (const x of name) {  
  // _code block to be executed_  
}

---

## Iterating Over an Array

You can use a `for..of` loop to iterate over the elements of an Array:

### Example

const letters = ["a","b","c"];  
  
for (const x of letters) {  
  // _code block to be executed_  
}