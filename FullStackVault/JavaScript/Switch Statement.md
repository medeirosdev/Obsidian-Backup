[[JS]]
The `switch` statement is used to perform different actions based on different conditions.

---
![[Pasted image 20220428092517.png]]


## The JavaScript Switch Statement

Use the `switch` statement to select one of many code blocks to be executed.

### Syntax

switch(_expression_) {  
  case _x_:  
    _// code block_    break;  
  case _y_:  
    _// code block_    break;  
  default:  
    // _code block_  
}

This is how it works:

-   The switch expression is evaluated once.
-   The value of the expression is compared with the values of each case.
-   If there is a match, the associated block of code is executed.
-   If there is no match, the default code block is executed.

### Example

The `getDay()` method returns the weekday as a number between 0 and 6.

(Sunday=0, Monday=1, Tuesday=2 ..)

This example uses the weekday number to calculate the weekday name:

switch (new Date().getDay()) {  
  case 0:  
    day = "Sunday";  
    break;  
  case 1:  
    day = "Monday";  
    break;  
  case 2:  
     day = "Tuesday";  
    break;  
  case 3:  
    day = "Wednesday";  
    break;  
  case 4:  
    day = "Thursday";  
    break;  
  case 5:  
    day = "Friday";  
    break;  
  case 6:  
    day = "Saturday";  
}

The result of day will be:

`Thursday`



## The break Keyword

When JavaScript reaches a `break` keyword, it breaks out of the switch block.

This will stop the execution inside the switch block.

It is not necessary to break the last case in a switch block. The block breaks (ends) there anyway.

**Note:** If you omit the break statement, the next case will be executed even if the evaluation does not match the case.

---

## The default Keyword

The `default` keyword specifies the code to run if there is no case match:

### Example

The `getDay()` method returns the weekday as a number between 0 and 6.

If today is neither Saturday (6) nor Sunday (0), write a default message:

switch (new Date().getDay()) {  
  case 6:  
    text = "Today is Saturday";  
    break;  
  case 0:  
    text = "Today is Sunday";  
    break;  
  default:  
    text = "Looking forward to the Weekend";  
}

The result of text will be:

`Looking forward to the Weekend`

The `default` case does not have to be the last case in a switch block:

### Example

switch (new Date().getDay()) {  
  default:  
    text = "Looking forward to the Weekend";  
    break;  
  case 6:  
    text = "Today is Saturday";  
    break;  
  case 0:  
    text = "Today is Sunday";  
}

If `default` is not the last case in the switch block, remember to end the default case with a break.