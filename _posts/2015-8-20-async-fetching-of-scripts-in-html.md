---
layout: post
title: Async fetching of script in HTML5
---

**Who wants a slow page loading? NO - ONE**  

If big external javascript file makes the loading of page slow, **what** can we do??

If my external scripts does not depend of the parsing of the page elements, then **why** should we load the script at the same time as html.

*Prereq* : [click this link to get more insights abouts the how html is loaded into the page ](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/#HTML_Parser)

One hack to overcome this page load time is to load the scripts in the seperate thread. This can be acheived by using **async** keyword in the script tag. 

``` html 
<script src="main.js" async></script>
```
This async key word in the script tag creates a seperate thread from rendering engine and loads the script asynchronously.

Another hack to load the script after the page is loaded (that is after all  the elements are parsed) is to use the **defer** attribute. 

``` html 
<script src="main.js" defer></script>
```

The following tables describes the action for async and defer.

 *Source:* [w3schools.com](http://www.w3schools.com/tags/att_script_defer.asp) 

| async 	| defer 	| Action  	|
| :----------|:---------:| :---------:|
| Yes 		| No 		| The script is executed asynchronously with the rest of the page (the script will be executed while the page continues the parsing) |
| No     | Yes      |  The script is executed when the page has finished parsing |
| No | No      | The script is fetched and executed immediately, before the browser continues parsing the page |


Thanks for reading. Now it is time to load faster. (personally i do use aync keyword for this site)


