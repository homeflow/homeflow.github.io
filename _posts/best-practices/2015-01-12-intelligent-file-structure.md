---
layout: default
title: Intelligent Code Design
modal-id: code-design
category: best-practices
---
At Homeflow we like to keep our code base nice and clean and well organized, this is important when designing a theme to be used on the Homeflow platform.

You should aim to keep your files small and concise, and to reuse code where possible using partials. For example, you may create a property partial which is reused in multiple areas throughout the site, not just the property pages. However, using **too many** partials (especially ones buried deep in the folder structure) can make a project difficult to read and navigate, especially for someone coming to the code for the first time. Bear this in mind and try to organise your code while keeping it readable.

You should also aim to keep your HTML and CSS code as clean as possible by removing unused or unnecessary code and formatting and indenting the files sensibly.

We would also advocate the use of code analysis tools like the [W3C Markup Validation Service](http://validator.w3.org/) or [CSS Validator](http://jigsaw.w3.org/css-validator/) to identify and fix problems in your code.  
