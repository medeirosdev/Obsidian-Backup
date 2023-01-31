[[JS]]
## Math.random()

`Math.random()` returns a random number between 0 (inclusive),  and 1 (exclusive):

### Example

// Returns a random number:  
Math.random();

`Math.random()` always returns a number lower than 1.

---

## JavaScript Random Integers

`Math.random()` used with `Math.floor()` can be used to return random integers.

There is no such thing as JavaScript integers.

We are talking about numbers with no decimals here.

### Example

// Returns a random integer from 0 to 9:  
Math.floor(Math.random() * 10);

### Example

// Returns a random integer from 0 to 10:  
Math.floor(Math.random() * 11);

### Example

// Returns a random integer from 0 to 99:  
Math.floor(Math.random() * 100);

### Example

// Returns a random integer from 0 to 100:  
Math.floor(Math.random() * 101);

### Example

// Returns a random integer from 1 to 10:  
Math.floor(Math.random() * 10) + 1;

### Example

// Returns a random integer from 1 to 100:  
Math.floor(Math.random() * 100) + 1;

