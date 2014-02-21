---
layout: post
title: "jquery enlightenment study notes 1"
date: 2014-02-19 20:14:00 +0800
comments: true
categories: jQuery
---
1. The central concept behind jQuery is, "find something, do something." More specifically, select DOM element(s) from an HTML document and then do something with them using jQuery methods.    
2. Also we can extend the concept behind jQuery to include,  first creating something new, selecting it, then doing something with it.     
3. Executing code when the DOM is ready, but before window.onload.   
4. Make sure all stylesheets are included before your jQuery code. Doing so will make sure all the elements in the DOM are correctly rendered before jQuery begins executing code.     
5. Typically we do not want to wait for the window.onload event. That is the point of using a custom event like ready() that will execute code before window loads, but after the DOM is ready to be traversed and manipulated.    
6. In fact, placing all JavaScript code at the bottom of a page is a proven performance strategy.    
7. When attaching events to DOM elements contained in a wrapper set, the keyword this can be used to refer to the current DOM element invoking the event.     
8. $('a').get(0).title = 'jQuery.com'; found become this: $('a')[0].title = 'jQuery.com'; Both allow access to the actual DOM element. For the square bracket notation, it i 
9. s faster because it uses native JavaScript to retrieve the element from an array, instead of passing it to a method.