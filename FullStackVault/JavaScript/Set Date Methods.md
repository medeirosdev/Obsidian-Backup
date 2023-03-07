[[JS]]
![[Pasted image 20220420180002.png]]

## The setFullYear() Method

The `setFullYear()` method sets the year of a date object. In this example to 2020:

### Example

const d = new Date();  
d.setFullYear(2020);  

The `setFullYear()` method can **optionally** set month and day:

### Example

const d = new Date();  
d.setFullYear(2020, 11, 3);