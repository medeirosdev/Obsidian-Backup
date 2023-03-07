[[JS HTML DOM]]
Learn to create HTML animations using JavaScript.

---

## A Basic Web Page

To demonstrate how to create HTML animations with JavaScript, we will use a simple web page:

### Example

<!DOCTYPE html>  
<html>  
<body>  
  
<h1>My First JavaScript Animation</h1>  
  
<div id="animation">My animation will go here</div>  
  
</body>  
</html>  

---

## Create an Animation Container

All animations should be relative to a container element.

### Example

<div id ="container">  
  <div id ="animate">My animation will go here</div>  
</div>

---

## Style the Elements

The container element should be created with style = "`position: relative`".

The animation element should be created with style = "`position: absolute`".

### Example

#container {  width: 400px;  
  height: 400px;  
  position: relative;  
  background: yellow;}  
#animate {  width: 50px;  
  height: 50px;  
  position: absolute;  
  background: red;}


## Animation Code

JavaScript animations are done by programming gradual changes in an element's style.

The changes are called by a timer. When the timer interval is small, the animation looks continuous.

The basic code is:

### Example

id = setInterval(frame, 5);  
  
function frame() {  
  if (/* test for finished */) {  
    clearInterval(id);  
  } else {  
    /* code to change the element style */   
  }  
}

---

## Create the Full Animation Using JavaScript

### Example

function myMove() {  
  let id = null;  
  const elem = document.getElementById("animate");  
  let pos = 0;  
  clearInterval(id);  
  id = setInterval(frame, 5);  
  function frame() {  
    if (pos == 350) {  
      clearInterval(id);  
    } else {  
      pos++;  
      elem.style.top = pos + 'px';  
      elem.style.left = pos + 'px';  
    }  
  }  
}
