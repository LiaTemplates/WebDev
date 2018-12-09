<!--
author:   Your Name

email:    your@mail.org

version:  0.0.1

language: en

narrator: US English Female

comment:  Try to write a short comment about
          your course, multiline is also okay.

@HTML: @__HTML(@uid)

@__HTML
<script>
    document.getElementById("@0").innerHTML = `@input`;
    "LIA: stop";
</script>

<div id="@0" class="persistent"></div>
@end

@JavaScript
<script>
let log = console.log;

send.lia("clr", "");

console.log = function(e){ send.lia("output", e+"\n") };

eval(`@input`)

console.log = log;

"LIA: stop";
</script>
@end



@HTML_JavaScript: @__HTML_JavaScript(@uid)

@__HTML_JavaScript
<script>
document.getElementById("@0").innerHTML = `@input`;

let log = console.log;

send.lia("clr", "");

console.log = function(e){ send.lia("output", e+"\n") };

eval(`@input(1)`)

console.log = log;

"LIA: stop";
</script>

<div id="@0" class="persistent"></div>
@end

-->

# WebDev Template

This short introduction presents the application of LiaScript for
WebDevelopment. The corresponding code is available on

https://github.com/liaScript/WebDev_template/edit/master/README.md

The presentation mode can be activated by clicking on

https://liascript.github.io/course/?https://raw.githubusercontent.com/liaScript/WebDev_template/master/README.md#1


## HTML

We start with a short HTML-snippet. Feel free extend or to change the code, afterwards you can evaluate
the output by clicking the blue execute button below the code box.

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
@HTML


## JavaScript

Ok, this was a static HTML example, but how can we add dynamic elements? We need
to include some lines of code ... let's start with some basics. Again, you can
adapt the code according to your project and test the algorithm immediately.
Please consider the version counter on the right, it offers the opportunity to
switch comfortably between different states of your code.

``` javascript for-loop.js
let fak = 1;

for(let i=1; i<10; i++) {
  fak = fak * i;
  console.log("i: " + i + "  fak:"+ fak);
}

console.log("fin")
```
@JavaScript


## HTML & JavaScript

Now we have to merge both worlds ... have fun :-)

```html index.html
<h1 id="hallo_id"> Hallo </h1>
```
```javascript  test.js
document.getElementById("hallo_id").innerHTML = "TEST";
```
@HTML_JavaScript
