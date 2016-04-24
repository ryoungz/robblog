---
layout: post
title:  "Coding Challenge #3 - Search And Filtering"
date:   2013-08-19 16:20:48 -0600
categories: jquery
permalink: Coding-Challenge-3
---
Search is one piece of functionality you find on almost all web pages now. This week’s challenge is a toe dip into the deep topic of search and filtering. We will build the functionality to allow users to do on page highlighting for text they enter in a search box.

jQuery, a JavaScript library, will be used to create this functionality. Once again we will break the task into small, digestible bits: 

1. We need to build a search form so users can enter in their term

2. We need some text to search through

3. Finally, we’ll write some JavaScript that gives us the search functionality.

## Search form

```html
Search Box:&nbsp;
<p><input id="searchterm" type="text" /></p>
```

## Content

The content we'll be filtering through is a few lines from the Constitution contained within HTML paragraph and div tags.

```html
<div class="replace">
    We the People of the United States, in Order to form a more perfect Union, establish Justice, insure domestic Tranquility, provide for the common defence, promote the general Welfare, and secure the Blessings of Liberty to ourselves and our Posterity, do ordain and establish this Constitution for the United States of America.</div>
<p class="replace">
    All legislative Powers herein granted shall be vested in a Congress of the United States, which shall consist of a Senate and House of Representatives.</p>
```

## Listener

Next we need to create a listener that monitors for text that is either typed or pasted into the search box. This is accomplished by binding our function to the keyup and change events from the jQuery library. A keyup event is sent when the user releases a key on the keyboard. The change event occurs when any changes happen to the element it is assigned to.

```javascript
$('#searchterm').bind("keyup change", function (e) {
var txt = $('#searchterm').val().trim();
var regex = new RegExp("(" + txt + ")", "igm");
```

## Highlight

Finally we need to display the results to the user. We'll write the functionality that replaces the search string entered by the user with a highlighted version of the same string (which is formatted using CSS).

```javascript
$('.replace').each(function () {
var stringSearch = $(this).text().replace(regex, "<span>$1</span>");
$(this).html(stringSearch);
});
```

View the full code at <a href="https://gist.github.com/ryoungz/6270596">https://gist.github.com/ryoungz/6270596</a>


