<img src="https://pbs.twimg.com/profile_images/682624238273097728/r1wr-8_t_reasonably_small.png" alt="StreamJar Logo"</img>

**StreamJar Custom CSS**
====================

Initial lists and examples produced by Rob Aimes (IAmOmicron) - http://aimes.eu


**This is NOT an official release or product of StreamJar!**

*Use this with caution. This is provided as an example and should only be taken as such.
I am not responsible for your CSS. Broken overlays are your own doing!*

This document gives some information on how to edit the StreamJar overlay elements with CSS
Some examples are provided for convinience.

A basic understanding of CSS is assumed.

---

Documentation:
--------------

***The CSS you create should be used on your OBS BrowserSource Settings***
	
To access an element a specific path is followed. This path is similar for all overlay elements. An example full path to an element is

`.overlay .canvas .element[data-type='song'] .image {`

[data-type]
-----------
		
In this example, we are looking at the elements with data-type 'song'. 

Wherever you encounter `[data-type='dataType']` the type can be replaced with one of the valid types listed below.

**Valid types:** 

* `song` 
* `notification'`
* `goal`
* `chat`
* `banner`
* `images` 
* `trigger` 
* `text`


[data-id]
---------
Since all of the elements are classes, if you have multiple elements of the same type on a single
overlay, they will all be changed unless given the '[data-id]' tag as well.

To change a specific element simply add the [data-id] tag directly after the [data-type] tag. **NO SPACE!**

For example:
	`[data-type='dataType'][data-id='dataID']`
	
The data-id for an element can be gained using the Google Chrome console. Go to your Streamjar account, click 'Launch Overlay' and copy the URL into your browser's address bar.

Simply open the console with F12 and use the 'point at' feature using `Ctrl + Shift + C` or click it in upper left hand corner of the window. Next to 'Toggle device mode'. 

<img src="https://raw.githubusercontent.com/iamomicron/StreamJarCSS/master/images/clickbutton.png" alt="StreamJar Logo"</img>

Click the element you wish to obtain the ID of and the HTML of that element should be highlighted in your console. Double click on the data-id tag to access it, and copy the long string inside. It should look similar to this and include both letters and numbers.

<img src="https://raw.githubusercontent.com/iamomicron/StreamJarCSS/master/images/grabID.png" alt="StreamJar Logo"</img>

**NOTE: Notifications are not visible in this view, but hovering over where they would be if active will allow you to select them.**

Some examples of what we have so far is:

```css
	.overlay .canvas .element[data-type='song'] {
	
	}
```

or

```css
	.overlay .canvas .element[data-type='song'][data-id='xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx'] {
	
	}
```


Down to Specifics
-----------------

StreamJar is well made in that each part of the overlay has it's own class. Using the above examples again; The album art, song name, artist title and the container that holds everything, are all separate.

These are easy to access. Take what you already know and go further along the path to the element. To access the 'container' (The visible box that holds all of the content) of the element, you need to check for the parent div like this:

```css
.overlay .canvas .element[data-type='song'] > div {
	
}
```

But, as another example. If you wish to access the album artwork on the currently playing song element, you do not need to access the div, as you are already inside the element. So instead, you could accomplish this like so:

```css
.overlay .canvas .element[data-type='song'] .image {
	
}
```

I do not currently have a *full* list of the sub-elements, but **[click here for an incomplete list.](https://github.com/iamomicron/StreamJarCSS/blob/master/subelements.md)**

***

Examples
--------

Using this knowledge you can now (hopefully) access any StreamJar element. Here are a couple of examples I use in my CSS.

* Rounded album artwork:

	```css
		.overlay .canvas .element[data-type='song'] .image {
			border-radius: 50px;
			box-shadow: none;
		}
	```
	
	From this:
	
	<img src="https://raw.githubusercontent.com/iamomicron/StreamJarCSS/master/images/artBefore.png" alt="StreamJar Logo" </img>
	
	to this:
	
	<img src="https://raw.githubusercontent.com/iamomicron/StreamJarCSS/master/images/artAfter.png" alt="StreamJar Logo"</img>

* Follower Notification - Profile picture to the right:

	```css
		.overlay .canvas .element[data-type='notification'][data-id=''] > div .image {
		float: right;
	}
	```

For more examples, please visit: https://github.com/iamomicron/StreamJarCSS/blob/master/examples.css
