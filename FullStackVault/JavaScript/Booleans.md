[[JS]]
A JavaScript Boolean represents one of two values: **true** or **false**.

---

## Boolean Values

Very often, in programming, you will need a data type that can only have one of two values, like

-   YES / NO
-   ON / OFF
-   TRUE / FALSE

For this, JavaScript has a **Boolean** data type. It can only take the values **true** or **false**.

---

## The Boolean() Function

You can use the `Boolean()` function to find out if an expression (or a variable) is true:

### Example

Boolean(10 > 9)

Or even easier:

### Example

(10 > 9)  
10 > 9

---

## Comparisons and Conditions

The chapter JS Comparisons gives a full overview of comparison operators.

The chapter JS Conditions gives a full overview of conditional statements.

Here are some examples:

## JavaScript Booleans as Objects

Normally JavaScript booleans are primitive values created from literals:

let x = false;

But booleans can also be defined as objects with the keyword `new`:

let y = new Boolean(false);

### Example

let x = false;  
let y = new Boolean(false);  
  
// typeof x returns boolean  
// typeof y returns object

Do not create Boolean objects.

The `new` keyword complicates the code and slows down execution speed.

Boolean objects can produce unexpected results: