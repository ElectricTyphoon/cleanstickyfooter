<h2>Example</h2>

<p><em>(updated 03/23/2013)</em></p>

<p>Due to the popularity of this technique, I've provided an example that shows it in action: <a href='http://cleanstickyfooter.herokuapp.com'>http://cleanstickyfooter.herokuapp.com</a> (note that cleanstickyfooter.css has an implementation similar to the overview below, but in a more succinct manner using classes and nested selectors). This project page will soon be updated to reflect what's in the example.</p>

<h2>Browser Compatibility Update</h2>

<p><em>(updated 03/30/2010)</em></p>

<p>This technique has been verified in ALL modern browsers. If you are experiencing any issues with this technique in IE8 (or any other browsers), please read this: <a href='http://code.google.com/p/cleanstickyfooter/issues/detail?id=2'>http://code.google.com/p/cleanstickyfooter/issues/detail?id=2</a></p>

<h2>Overview</h2>

<p><em>(updated 08/12/2009)</em></p>

<p>Over the past couple of months I have run across a few "sticky footer" techniques. While these techniques are okay, I felt that they were a little to invasive with their hacks, such as using the "clear fix" hack.</p>

<p>About a year ago I had to conquer the "sticky footer" problem on a project I was working on. Ever since then I have been refining my technique, and feel that now it's a perfect time to release what I like to call the "cleanStickyFooter".</p>

<p>There is only one hack, which is a height targeting hack for Internet Explorer 6 and older browsers like it.</p>

<h2>The HTML</h2>

<p>Lets start off by building out the basic HTML needed for this technique.</p>

```


<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">

<head>

<title>cleanStickyFooter

Unknown end tag for &lt;/title&gt;



<link rel="stylesheet" type="text/css" href="cleanstickyfooter.css" media="screen" charset="utf-8" />

<link rel="stylesheet" type="text/css" href="styles.css" media="screen" charset="utf-8" />



Unknown end tag for &lt;/head&gt;



<body>

<div id="wrapper">

<div id="content_wrapper">

<div id="content_inner_wrapper">

<div>Site content will be contained here.

Unknown end tag for &lt;/div&gt;





Unknown end tag for &lt;/div&gt;





Unknown end tag for &lt;/div&gt;





Unknown end tag for &lt;/div&gt;



<div id="footer_wrapper">

<div id="footer_inner_wrapper">

<div>The footer's content

Unknown end tag for &lt;/div&gt;





Unknown end tag for &lt;/div&gt;





Unknown end tag for &lt;/div&gt;





Unknown end tag for &lt;/body&gt;





Unknown end tag for &lt;/html&gt;



```

<p>Looking at the HTML below, you see a div with the id of "content_inner_wrapper", the inner wrapper is only used if you have a site where you have a centered content area. In our case we do, so we add this div in. Same rules apply for the "footer_inner_wrapper" inside of "footer_wrapper".</p>

```


<div id="content_inner_wrapper">

<div>Site content will be contained here.

Unknown end tag for &lt;/div&gt;





Unknown end tag for &lt;/div&gt;



```

<h2>The CSS</h2>

<p>I am going to start off by showing all of the required CSS to make this work (except the last two lines), then break it down line by line.</p>

```


html, body {
height: 100%;
}

body {
margin: 0px;
padding: 0px;
}

div#wrapper {
width: 100%;
min-height: 100%;
height: auto !important;
height: 100%;
margin: 0px 0px -41px 0px;
}

div#footer_wrapper {
width: 100%;
height: 41px;
}

div#content_wrapper {
width: 100%;
padding: 0px 0px 41px 0px;
}

div#footer_wrapper, div#content_wrapper {
min-width: 942px;
}

div#footer_inner_wrapper, div#content_inner_wrapper {
width: 942px;
margin: 0px auto;
}

```

<h4>Required</h4>

<p>First starting off with the "html, body" selector, we are going to set not only the body but the html tag to a height of 100%, without the html tag at a height of 100% this wont work.</p>

```


html, body {
height: 100%;
}

```

<p>Next if not already done so, want to clear the default margin the browser applies.</p>

```


body {
margin: 0px;
padding: 0px;
}

```

<p>The next block is the most crucial. In this block we are going to do the following:<br />1. Set the width of the wrapper to 100% (not required but semantically makes sense because the footer is at the same level and is at a width of 100%, also useful if you want a header that is a width of 100%, you would contain the header inside of div#wrapper).<br />2. Give the wrapper a min-height of 100% (min-height doesn't work well in IE6 and older browsers like it, so we are going to set the height to "auto" and make sure it has the "!important" flag so our new browsers don't pick up on the next line).<br />3. In the next like we are simply using height: 100%, it will act as min height in the older browsers (older browsers allow expanding heights).<br />4. Then we are going to set a bottom margin to the negative version of the height of the footer. In our case the footer is 41px high, so our bottom margin is -41px.</p>

```


div#wrapper {
width: 100%;
min-height: 100%;
height: auto !important;
height: 100%;
margin: 0px 0px -41px 0px;
}

```

<p>The footer wrapper we will simply asign a height, the above block pushes everything down for us. We will also push this div out to a width of 100%.</p>

```


div#footer_wrapper {
width: 100%;
height: 41px;
}

```

<p>The main deal with the next block is we need to set a bottom padding of 41px to counteract the -41px margin we set above. We are also setting a width of 100%.</p>

```


div#content_wrapper {
width: 100%;
padding: 0px 0px 41px 0px;
}

```

<h4>Required in certain cases</h4>

<p>Use the next two below if you have all of your content in a centered containing div, in our case the div is 942px wide. If not, disregard the following two blocks.</p>

<p>Use the block below when the content is scrolled horizontally, we will want to set a min-width on the footer_wrapper and the content_wrapper. The min-width should be the width of the container (see the next block below). Without this there will be a gap of empty space on the right side. Min-width will work in older versions of IE if you have a width set above, in our case we have a width of 100% set.</p>

<p>To see what I'm talking about here, simply remove the min-width, and refresh your page. Make sure you scroll in enough where you see the horizontal scroll bar. Then scroll to the right, you will see an empty area. Now put that min-width back in there :)</p>

```


div#footer_wrapper, div#content_wrapper {
min-width: 942px;
}

```

<p>Lastly we are going to set the width of our container for the content. We are also going to center the container by using the common margin: 0px auto.</p>

```


div#footer_inner_wrapper, div#content_inner_wrapper {
width: 942px;
margin: 0px auto;
}

```

<h2>Browsers</h2>

<p>This has been tested in Firefox (2, 3, 3.5), Internet Explorer (6, 7, 8), Safari, Opera, & Google Crome.</p>

<h2>The Difference</h2>

<p>Google "sticky footer", I have listed below why this technique works better than the top results from this search.</p>

<p><a href='http://ryanfait.com/sticky-footer/'>http://ryanfait.com/sticky-footer/</a> - This technique is similar, but cleanStickyFooter takes it much further. The technique located here doesn't play nicely when you want to make your footer have a width of 100%.</p>

<p><a href='http://www.cssstickyfooter.com/'>http://www.cssstickyfooter.com/</a> - This technique is one out of many I am referring to when I say its invasive with CSS clearing hacks.</p>

<p>I think I will stop there, do some research yourself (if you haven't already done so) and you will see most techniques use z-indexes and clearing hacks, when they really aren't necessary.</p>