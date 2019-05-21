<!--
author:   André Dietrich

email:    andre.dietrich@ovgu.de

version:  0.1.0

language: en

narrator: US English Female

comment:  A set of macros, that can be used for teachning (front-end)
          web-development, including (HTML and JavaScript).


@WebDev.HTML: @WebDev._HTML(@uid)
@WebDev._HTML
<script>
    document.getElementById("@0").innerHTML = `@input`;
    "LIA: stop";
</script>

<div id="@0"></div>
@end

@WebDev.JS
<script>
let rslt = eval(`@input`);
console.log(rslt);
"LIA: stop";
</script>
@end

@WebDev.HTML_CSS: @WebDev._HTML_CSS(@uid)
@WebDev._HTML_CSS
<script>
let iframe = document.getElementById("@0");
iframe.hidden = false;
iframe.style.height = "10px";
iframe.contentDocument.documentElement.innerHTML  = `<style scoped>@input(1)</style>@input`;
iframe.style.height = getDocHeight( iframe ) + 4 + "px";
"LIA: stop";
</script>

<iframe id="@0" style="width: 100%" hidden="true"></iframe>
@end


@WebDev.HTML_JS: @WebDev._HTML_JS(@uid)
@WebDev._HTML_JS
<script>
document.getElementById("@0").innerHTML = `@input`;
eval(`@input(1)`);
"LIA: stop";
</script>

<div id="@0"></div>
@end

@onload
window.getDocHeight = function(doc) {
    doc = doc.contentDocument? doc.contentDocument : doc.contentWindow.document;
    // stackoverflow.com/questions/1145850/
    var body = doc.body, html = doc.documentElement;
    var height = Math.max( body.scrollHeight, body.offsetHeight,
        html.clientHeight, html.scrollHeight, html.offsetHeight );
    return height;
};
@end
-->

# WebDev - Template

                         --{{0}}--
This document defines basic macros, to be used in
[LiaScript](https://LiaScript.github.io), that can be used for teaching
(front-end) web-development. By adding these macros to the end of one or two
Markdown code-blocks, they will be made editable and executable.

__Try it on LiaScript:__

https://liascript.github.io/course/?https://raw.githubusercontent.com/liaTemplates/WebDev/master/README.md

__See the project on Github:__

https://github.com/liaTemplates/WebDev


                         --{{1}}--
There are three ways to use this template. The easiest way is to use the
`import` statement and the url of the raw text-file of the master branch or any
other branch or version. But you can also copy the required functionionality
directly into the header of your Markdown document, see therefor the
[last slide](#5). And of course, you could also clone this project and change
it, as you wish.

                           {{1}}
1. Load the macros via

   `import: https://raw.githubusercontent.com/liaTemplates/WebDev/master/README.md`

2. Copy the definitions into your Project

3. Clone this repository on GitHub

## `@WebDev.HTML`

                         --{{0}}--
We start with a short HTML-snippet. Feel free extend or to change the code,
afterwards you can evaluate the output by clicking onto the execute button below
the code box.

``` html table.html
<h1>This is an example of a table</h1>

Feel free to change the code and to test the output by clicking the execute button below the code box.

<table>
  <tr>
    <th style="text-align:left"> Header 1 </th>
    <th style="text-align:left"> Header 2 </th>
  </tr>
  <tr>
    <td style="text-align:left"> row 1.1 </td>
    <td style="text-align:left"> row 1.2 </td>
  </tr>
  <tr>
    <td style="text-align:left"> row 2.1 </td>
    <td style="text-align:left"> row 2.2 </td>
  </tr>
</table>
```
@WebDev.HTML


## `@WebDev.JS`

                         --{{0}}--
Ok, this was a static HTML example, but how can we add dynamic elements? We need
to include some lines of code ... Let's start with some basics. Again, you can
adapt the code according to your project and test the algorithms immediately.
See the version counter on the right, it offers the opportunity to switch
comfortably between different states of your code.

``` js for-loop.js
let fak = 1;

for(let i=1; i<10; i++) {
  fak = fak * i;
  console.log("i: ", i ,"  fak:", fak);
}

console.log("fin")
```
@WebDev.JS


## `@WebDev.HTML_CSS`

                         --{{0}}--
Styling HTML with CSS is enabled by this macro (`@WebDev.HTML_CSS`). Two
succeeding code-blocks have to be defined, whereby the first contains the HTML
content and the second one holdes the CSS.

``` html style.html
<div>
  <h1>Test</h1>
</div>
```
``` css  style.css
div {border: 2px solid black; background-color: blue;}
```
@WebDev.HTML_CSS


## `@WebDev.HTML_JS`

                         --{{0}}--
Combining HTML and JavaScript is enabled by this macro (`@WebDev.HTML_JS`). Two
succeeding code-blocks have to be defined, whereby the first contains the HTML
content and the second one holdes the JavaScript to be executed.

```html index.html
<h1 id="hallo_id"> Hallo </h1>
```
```js  test.js
document.getElementById("hallo_id").innerHTML = "TEST";
```
@WebDev.HTML_JS


## Implementation

                         --{{0}}--
The code shows how the macros were implemented. Most of them make use of a
hidden  macro, starting with and underscore. This way, it is possible to hide
also the usage of the `@uid` macro, which is required to generate a unique
identifier, which defines the ids of the associated `divs` and `iframes`. The
`@onload` macro is a special one, which is called once after the loading of a
document. This way some initialization can be implemented.


``` html
@WebDev.HTML: @WebDev._HTML(@uid)
@WebDev._HTML
<script>
    document.getElementById("@0").innerHTML = `@input`;
    "LIA: stop";
</script>

<div id="@0"></div>
@end


@WebDev.JS
<script>
let rslt = eval(`@input`);
console.log(rslt);
"LIA: stop";
</script>
@end


@WebDev.HTML_CSS: @WebDev._HTML_CSS(@uid)
@WebDev._HTML_CSS
<script>
let iframe = document.getElementById("@0");
iframe.hidden = false;
iframe.style.height = "10px";
iframe.contentDocument.documentElement.innerHTML  = `<style scoped>@input(1)</style>@input`;
iframe.style.height = getDocHeight( iframe ) + 4 + "px";
"LIA: stop";
</script>

<iframe id="@0" style="width: 100%" hidden="true"></iframe>
@end


@WebDev.HTML_JS: @WebDev._HTML_JS(@uid)
@WebDev._HTML_JS
<script>
document.getElementById("@0").innerHTML = `@input`;
eval(`@input(1)`);
"LIA: stop";
</script>

<div id="@0"></div>
@end


@onload
window.getDocHeight = function(doc) {
  doc = doc.contentDocument? doc.contentDocument : doc.contentWindow.document;
  // stackoverflow.com/questions/1145850/
  var body = doc.body, html = doc.documentElement;
  var height = Math.max( body.scrollHeight, body.offsetHeight,
      html.clientHeight, html.scrollHeight, html.offsetHeight );
  return height;
};
@end
```

                         --{{1}}--
If you want to minimize loading effort in your LiaScript project, you can also
copy this code and paste it into your main comment header, see the code in the
raw file of this document.

{{1}} https://raw.githubusercontent.com/liaTemplates/WebDev/master/README.md
