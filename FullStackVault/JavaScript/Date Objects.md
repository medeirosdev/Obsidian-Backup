[[JS]]
### Example

const d = new Date();  

---

## JavaScript Date Output

By default, JavaScript will use the browser's time zone and display a date as a full text string:

**Wed Apr 20 2022 17:48:00 GMT-0300 (Brasilia Standard Time)**

You will learn much more about how to display dates, later in this tutorial.

---

## Creating Date Objects

Date objects are created with the `new Date()` constructor.

There are **4 ways** to create a new date object:

new Date()  
new Date(_year, month, day, hours, minutes, seconds, milliseconds_)  
new Date(_milliseconds_)  
new Date(_date string_)  

---

## new Date()

`new Date()` creates a new date object with the **current date and time**:

### Example

const d = new Date();

Date objects are static. The computer time is ticking, but date objects are not.

---

## new Date(_year, month, ..._)

`new Date(_year, month, ..._)` creates a new date object with a **specified date and time**.

7 numbers specify year, month, day, hour, minute, second, and millisecond (in that order):

### Example

const d = new Date(2018, 11, 24, 10, 33, 30, 0);

**Note:** JavaScript counts months from **0** to **11**:

**January = 0**.

**December = 11**.

Specifying a month higher than 11, will not result in an error but add the overflow to the next year:

Specifying:

const d = new Date(2018, 15, 24, 10, 33, 30);  

Is the same as:

const d = new Date(2019, 3, 24, 10, 33, 30);  

Specifying a day higher than max, will not result in an error but add the overflow to the next month:

Specifying:

const d = new Date(2018, 5, 35, 10, 33, 30);  

Is the same as:

const d = new Date(2018, 6, 5, 10, 33, 30);  

---

## Using 6, 4, 3, or 2 Numbers

6 numbers specify year, month, day, hour, minute, second:

### Example

const d = new Date(2018, 11, 24, 10, 33, 30);  

5 numbers specify year, month, day, hour, and minute:

### Example

const d = new Date(2018, 11, 24, 10, 33);  

4 numbers specify year, month, day, and hour:

### Example

const d = new Date(2018, 11, 24, 10);  

3 numbers specify year, month, and day:

### Example

const d = new Date(2018, 11, 24);  

2 numbers specify year and month:

### Example

const d = new Date(2018, 11);  

You cannot omit month. If you supply only one parameter it will be treated as milliseconds.

## JavaScript Stores Dates as Milliseconds

JavaScript stores dates as number of milliseconds since January 01, 1970, 00:00:00 UTC (Universal Time Coordinated).

Zero time is January 01, 1970 00:00:00 UTC.

Now the time is: **1650487680061** milliseconds past January 01, 1970

---

## new Date(_milliseconds_)

`new Date(_milliseconds_)` creates a new date object as **zero time plus milliseconds**:

### Example

const d = new Date(0);

01 January 1970 **plus** 100 000 000 000 milliseconds is approximately 03 March 1973:

### Example

const d = new Date(100000000000);

January 01 1970 **minus** 100 000 000 000 milliseconds is approximately October 31 1966:

## JavaScript Date Input

There are generally 3 types of JavaScript date input formats:

Type

Example

ISO Date

"2015-03-25" (The International Standard)

Short Date

"03/25/2015"

Long Date

"Mar 25 2015" or "25 Mar 2015"

The ISO format follows a strict standard in JavaScript.

The other formats are not so well defined and might be browser specific.

---

## JavaScript Date Output

Independent of input format, JavaScript will (by default) output dates in full text string format:

Wed Apr 20 2022 17:50:16 GMT-0300 (Brasilia Standard Time)

---

## JavaScript ISO Dates

ISO 8601 is the international standard for the representation of dates and times.

The ISO 8601 syntax (YYYY-MM-DD) is also the preferred JavaScript date format:

### Example (Complete date)

const d = new Date("2015-03-25");

The computed date will be relative to your time zone.  
Depending on your time zone, the result above will vary between March 24 and March 25.

![[Pasted image 20220420175101.png]]