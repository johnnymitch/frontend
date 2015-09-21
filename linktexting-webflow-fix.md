# How to fix issue when using Linktexting on a Webflow site

## The issue
When you hit the submit button, you get the following error returned in the console:

TypeError: $("#numberToText_linkTexting_"+t).intlTelInput is not a function. (In '$("#numberToText_linkTexting_"+t).intlTelInput("getNumber")', '$("#numberToText_linkTexting_"+t).intlTelInput' is undefined)
sendLink_linkTextinglink_texting.min.js:1:22777
onclickbackpacker:96

## The reason
This happens because both LinkTexting & Webflow are referencing Jquery. As Linktexting calls it in the <head>, and Webflow calls it in the <footer>, they conflict.

## The solution
Take the following code out of the Linktexting embed, and put it into the <head> of Webflow under "custom code"

<!-- Linktexting -->
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
<link rel="stylesheet" href="http://d3q6uu7asevdsg.cloudfront.net/1.3/css/link_texting.min.css">

Then, when you download the site, scroll to the bottom of the index.html file and comment out the following line:

<script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>

## Conclusion
Problem solved!
