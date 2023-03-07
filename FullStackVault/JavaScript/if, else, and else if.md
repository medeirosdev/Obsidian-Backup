## Conditional Statements
[[JS]]
Very often when you write code, you want to perform different actions for different decisions.

You can use conditional statements in your code to do this.

In JavaScript we have the following conditional statements:

-   Use `if` to specify a block of code to be executed, if a specified condition is true
-   Use `else` to specify a block of code to be executed, if the same condition is false
-   Use `else if` to specify a new condition to test, if the first condition is false
-   Use `switch` to specify many alternative blocks of code to be executed

The `switch` statement is described in the next chapter.

---

## The if Statement

Use the `if` statement to specify a block of JavaScript code to be executed if a condition is true.

### Syntax

if (_condition_) {  
  //  _block of code to be executed if the condition is true_}

Note that `if` is in lowercase letters. Uppercase letters (If or IF) will generate a JavaScript error.

### Example

Make a "Good day" greeting if the hour is less than 18:00:

if (hour < 18) {  
  greeting = "Good day";  
}

The result of greeting will be:

`Good day`

## The else Statement

Use the `else` statement to specify a block of code to be executed if the condition is false.

if (_condition_) {  
  //  _block of code to be executed if the condition is true_} else {  
  //  _block of code to be executed if the condition is false_}

### Example

If the hour is less than 18, create a "Good day" greeting, otherwise "Good evening":

if (hour < 18) {  
  greeting = "Good day";  
} else {  
  greeting = "Good evening";  
}

The result of greeting will be:

`Good day`

---

## The else if Statement

Use the `else if` statement to specify a new condition if the first condition is false.

### Syntax

if (_condition1_) {  
  //  _block of code to be executed if condition1 is true_} else if (_condition2_) {  
  //  _block of code to be executed if the condition1 is false and condition2 is true_  
} else {  
  //  _block of code to be executed if the condition1 is false and condition2 is false_}

### Example

If time is less than 10:00, create a "Good morning" greeting, if not, but time is less than 20:00, create a "Good day" greeting, otherwise a "Good evening":

if (time < 10) {  
  greeting = "Good morning";  
} else if (time < 20) {  
  greeting = "Good day";  
} else {  
  greeting = "Good evening";  
}

The result of greeting will be:

`Good day`

