# Ajax Cheatsheet


### XML HTTP Request

```javascript
var request = new XMLHttpRequest();
request.open('GET', 'https://ajax-resource-url.com/resource/');
request.send();
request.onload = function() {
  console.log(JSON.parse(request.response));
}
```

### Fetch

```javascript
fetch("https://ajax-resource-url.com/resource"
).then(response => {
      return response.json(); 
}).then(data => {
      console.log(data);
});
```

### Jquery AJAX

```javascript
$(document).ready(function(){

  $.ajax({
      url: "https://ajax-resource-url.com/resource",
      type: "GET",
      success: function(result) {
          console.log(result);
      }
  });

});
```

### Axios

```javascript
axios.get("https://ajax-resource-url.com/resource").then(response => {
    console.log(response.data);
});
```

# Ajax with Django

views.py

```python
# ...
from django.http import JsonResponse

# This is a simple django view
def home(request):
  # ...
  return render(request, "template/home.html", data)

# This is an AJAX view that returns a JSON object
def get_posts(request):
    all_posts = Post.objects.all().values()
    response = {
        'all_posts': list(all_posts),
    }
    return JsonResponse(response)
```
The `JsonResponse` class returns an HTTP response with an application/json content type, converting the given object into a JSON object

urls.py
```python
from django.urls import path
from .views import  home, get_posts

urlpatterns = [
    path('', home, name='home'),
    path('get_posts', get_posts, name='get_posts')
]
```
html
```html

<script>

    // DOM Elements
    var demo_div = document.getElementById("demo-div");
    var ajax_button = document.getElementById("ajax-button");

    // AJAX Call
    ajax_button.onclick = function(event) {
      event.preventDefault();

      const xhttp = new XMLHttpRequest();

      xhttp.onload = function() {
        const json_obj = JSON.parse(this.responseText)

        for (var i=0; i < json_obj["all_posts"].length; i++) {
          demo_div.innerHTML += `
            <div style="display: block; border: 1px solid black; margin-bottom:10px">
              <h1>${json_obj["all_posts"][i]["content"]}</h1>
            </div>
          `
        }
      }

      xhttp.open("GET", "/get_all_posts/");
      xhttp.send();
    }


  </script>
```

## Timeout 502 Error Fix

In ajax if your call is longer than 30secs first you need to have a timeout parameter for your call and your server of choice should be able to handle that aswell, lets look at nginx and a ajax call tohether:
```html
$.ajax({
      url: '...'
      type: "GET",
      timeout:600000,
      success: function(result) { }
});
```
And in nginx write these:
```
...
```


