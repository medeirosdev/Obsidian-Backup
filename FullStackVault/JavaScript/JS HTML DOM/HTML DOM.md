The HTML DOM allows JavaScript to change the content of HTML elements.
[[JS HTML DOM]]
---

## Changing HTML Content

The easiest way to modify the content of an HTML element is by using the `innerHTML` property.

To change the content of an HTML element, use this syntax:

document.getElementById(_id_).innerHTML = _new HTML_

This example changes the content of a `<p>` element:

### Example

<html>  
<body>  
  
<p id="p1">Hello World!</p>  
  
<script>  
document.getElementById("p1").innerHTML = "New text!";  
</script>  
  
</body>  
</html>

Example explained:

-   The HTML document above contains a `<p>` element with `id="p1"`
-   We use the HTML DOM to get the element with `id="p1"`
-   A JavaScript changes the content (`innerHTML`) of that element to "New text!"

This example changes the content of an `<h1>` element:

### Example

<!DOCTYPE html>  
<html>  
<body>  
  
<h1 id="id01">Old Heading</h1>  
  
<script>  
const element = document.getElementById("id01");  
element.innerHTML = "New Heading";  
</script>  
  
</body>  
</html>

Example explained:

-   The HTML document above contains an `<h1>` element with `id="id01"`
-   We use the HTML DOM to get the element with `id="id01"`
-   A JavaScript changes the content (`innerHTML`) of that element to "New Heading"


## Changing the Value of an Attribute

To change the value of an HTML attribute, use this syntax:

document.getElementById(_id_)._attribute = new value_

This example changes the value of the src attribute of an `<img>` element:

### Example

<!DOCTYPE html>  
<html>  
<body>  
  
<img id="myImage" src="smiley.gif">  
  
<script>  
document.getElementById("myImage").src = "landscape.jpg";  
</script>  
  
</body>  
</html>

Example explained:

-   The HTML document above contains an `<img>` element with `id="myImage"`
-   We use the HTML DOM to get the element with `id="myImage"`
-   A JavaScript changes the `src` attribute of that element from "smiley.gif" to "landscape.jpg"

---

## Dynamic HTML content

JavaScript can create dynamic HTML content:

Date : Tue Apr 26 2022 16:19:12 GMT-0300 (Brasilia Standard Time)

### Example

<!DOCTYPE html>  
<html>  
<body>  
  
<script>document.getElementById("demo").innerHTML = "Date : " + Date(); </script>  
  
</body>  
</html>

---

## document.write()

In JavaScript, `document.write()` can be used to write directly to the HTML output stream:

### Example

<!DOCTYPE html>  
<html>  
<body>  
  
<p>Bla bla bla</p>  
  
<script>  
document.write(Date());  
</script>  
  
<p>Bla bla bla</p>  
  
</body>  
</html>

Never use `document.write()` after the document is loaded. It will overwrite the document.