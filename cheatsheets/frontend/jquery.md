# Jquery

jQuery is a lightweight, "write less, do more", JavaScript library. jQuery also simplifies a lot of the complicated things from JavaScript, like AJAX calls and DOM manipulation.

## Installation

There are several ways to start using jQuery on your web site. You can:
- Download the jQuery library from jQuery.com
- Include jQuery from a CDN, like Google

CDN Example:
```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
```

## Getting Started

With jQuery you select (query) HTML elements and perform "actions" on them.

Basic syntax is: `$(selector).action()`
- A $ sign to define/access jQuery
- A (selector) to "query (or find)" HTML elements
- A jQuery action() to be performed on the element(s)

```javascript
$(this).hide() // hides the current element.
$("p").hide()  // hides all the p elements
$(".test").hide() // hides all elements with class="test"
$("#test").hide() // hides the element with id="test"


$(document).ready(function(){

  // All jQuery methods go into this document event because
  // this prevents the browser running the jquery before the
  // HTML and CSS is loaded. It is a good practice

});

// Few Selector Examples
$("*") // Selects all elements
$(this) // Sets the current HTML element
$("p.intro") // Selects all <p> elements with class="intro"
$("p:first") // Selects the first <p> element

```

Events:
```javascript
// You can have a single event bind to a 
// selector or you can chain multiple with "on" keyword

$("p").click(function(){
  // single event
});


// Chained binding
$("p").on({
  mouseenter: function(){
    $(this).css("background-color", "lightgray");
  },
  mouseleave: function(){
    $(this).css("background-color", "lightblue");
  },
  click: function(){
    $(this).css("background-color", "yellow");
  }
});

```

## jQuery Effects

```javascript
$("p").hide();  // hides the element
$("p").show();  // shows the element

// fade in and out for elements
$("button").click(function(){
  $("#div1").fadeIn();
  $("#div2").fadeIn("slow");
  $("#div3").fadeIn(3000);
});
```

View all [effects reference](https://www.w3schools.com/jquery/jquery_ref_effects.asp)

## jQuery Traversing

```javascript
$("span").parent();
$("div").children();
$("h2").siblings();
$("h2").next();
$("div").first();

// and much more ... check jquery
// traversing in reference docs
```

## jQuery AJAX

### LOAD 

syntax:
```
$(selector).load(URL,data,callback);
```
- The required URL parameter specifies the URL you wish to load.
- The optional data parameter specifies a set of querystring key/value pairs to send along with the request.
- The optional callback parameter is the name of a function to be executed after the load() method is completed.

jquery example:
```javascript
$(document).ready(function(){

  $("button").click(function(){
    $("#div1").load("demo_test.txt");
  });
  
});
```

The optional callback parameter specifies a callback function to run when the load() method is completed. The callback function can have different parameters:
- `responseTxt` - contains the resulting content if the call succeeds
- `statusTxt` - contains the status of the call
- `xhr` - contains the XMLHttpRequest object

```javascript
$("button").click(function(){
  $("#div1").load("demo_test.txt", function(responseTxt, statusTxt, xhr){
    if(statusTxt == "success")
      alert("External content loaded successfully!");
    if(statusTxt == "error")
      alert("Error: " + xhr.status + ": " + xhr.statusText);
  });
});
```

### GET/POST

The jQuery get() and post() methods are used to request data from the server with an HTTP GET or POST request.

#### GET Request syntax:
```
$.get(URL, callback);
``` 
example:
```javascript
$("button").click(function(){
  $.get("demo_test.asp", function(data, status){
    alert("Data: " + data + "\nStatus: " + status);
  });
});
```
The second parameter is a callback function. The first callback parameter holds the content of the page requested, and the second callback parameter holds the status of the request.

#### POST Request Syntax:
```
$.post(URL,data,callback);
```
example:
```javascript
$("button").click(function(){
  $.post("demo_test_post.asp",
  {
    name: "Donald Duck",
    city: "Duckburg"
  },
  function(data, status){
    alert("Data: " + data + "\nStatus: " + status);
  });
});
```
- The first parameter of $.post() is the URL we wish to request ("demo_test_post.asp").
- Then we pass in some data to send along with the request (name and city).
- The ASP script in "demo_test_post.asp" reads the parameters, processes them, and returns a result.
- The third parameter is a callback function. The first callback parameter holds the content of the page requested, and the second callback parameter holds the status of the request.






