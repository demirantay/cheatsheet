# Js Slider

```html
{% extends 'base.html' %}
{% load static %}

{% block css_link %}
<link rel="stylesheet" type="text/css" href="{% static 'css/base.css' %}" />

<style>
.main-screen img {
  height: 200px;
  width: 200px;
  background-color: grey;
  display: block;
  display: none;
}

.small-screen {
  height: 75px;
  width: 75px;
  display: inline-block;
  margin-top: 10px;
}

.small-screen:hover {
  cursor: pointer;
}


</style>

{% endblock %}

{% block content %}
<h3>Test</h3>

<button onclick="plusDivs(-1)">❮ Prev</button>
<button onclick="plusDivs(1)">Next ❯</button>

<Br />
<Br />

<div class="main-screen">
  <img src="{{ current_data.img1.url }}" class="main-screen-slide" />
  <img src="{{ current_data.img2.url }}" class="main-screen-slide" />
  <img src="{{ current_data.img3.url }}" class="main-screen-slide" />
  <img src="{{ current_data.img4.url }}" class="main-screen-slide" />
</div>

<img id="small-screen-1" class="small-screen" src="{{ current_data.img1.url }}" onclick="currentDiv(1)" />
<img id="small-screen-1" class="small-screen" src="{{ current_data.img2.url }}" onclick="currentDiv(2)" />
<img id="small-screen-1" class="small-screen" src="{{ current_data.img3.url }}" onclick="currentDiv(3)" />
<img id="small-screen-1" class="small-screen" src="{{ current_data.img4.url }}" onclick="currentDiv(4)" />


<script>
  //


  // Slider Algorithm
  var slideIndex = 1;
  showDivs(slideIndex);

  function plusDivs(n) {
    showDivs(slideIndex += n);
  }

  function currentDiv(n) {
    showDivs(slideIndex = n);
  }

  function showDivs(n) {
    var i;
    var x = document.getElementsByClassName("main-screen-slide");
    var dots = document.getElementsByClassName("small-screen");
    if (n > x.length) {slideIndex = 1}
    if (n < 1) {slideIndex = x.length}
    for (i = 0; i < x.length; i++) {
      x[i].style.display = "none";
    }
    for (i = 0; i < dots.length; i++) {
      dots[i].className = dots[i].className.replace(" w3-red", "");
    }
    x[slideIndex-1].style.display = "block";
    dots[slideIndex-1].className += " w3-red";
  }


</script>

{% endblock %}


```