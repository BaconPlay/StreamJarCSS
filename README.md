<img src="https://pbs.twimg.com/profile_images/682624238273097728/r1wr-8_t_reasonably_small.png" alt="StreamJar Logo"</img>

**StreamJar Custom CSS (OBS)**
====================

Initial lists and examples produced by Rob Aimes (IAmOmicron) - http://aimes.eu

**This is NOT an official release or product of StreamJar!**

**As this is unofficial, this method may stop working at any time.**

*Use this with caution. This is provided as an example and should only be taken as such.
I am not responsible for your CSS. Broken overlays are your own doing!*

This document gives some information on how to edit the StreamJar overlay elements with CSS.
Some examples are provided for convinience.

A basic understanding of CSS is assumed.


***


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

<center><img src="https://raw.githubusercontent.com/iamomicron/StreamJarCSS/master/images/clickbutton.png" alt="StreamJar Logo"</img></center>

Click the element you wish to obtain the ID of and the HTML of that element should be highlighted in your console. Double click on the data-id tag to access it, and copy the long string inside. It should look similar to this and include both letters and numbers.

<center><img src="https://raw.githubusercontent.com/iamomicron/StreamJarCSS/master/images/grabID.png" alt="StreamJar Logo"</img></center>

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

StreamJar is well made in that each part of the overlay has it's own class. Using the song examples again; The album art, song name, artist title and the container that holds everything, are all separate.

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



!important
----------

Some elements in streamjar have their style set inline, via HTML. When this is the case, the !important tag may be required for your custom CSS to take effect. A telltale example of how you know when to use this, is when you set CSS on an element and the CSS does not take effect. If certain changes did not take effect when you expected a change, you most likely need to use the `!important` tag.

An example of something that now requires this, is the `.chat . messages > div` element when setting the background colour. Take the below code that assigns a cyan background to the 'beam' messages.

```css
	.overlay .canvas .element[data-type='chat'] > .chat > .messages > div {
		background-color: rgb(0, 255, 255);
	}
```

Where you have the line `background-color:` to set the background colour, simply add the `!important` tag before the line end. The code should now look similar to below, and should also now correctly apply the CSS:

```css
	.overlay .canvas .element[data-type='chat'] > .chat > .messages > div {
		background-color: rgb(0, 255, 255) !important;
	}
```


[data-platform] & .chat
---------------

When using the StreamJar chat overlay, each message has a `[data-platform]` tag applied to it's div element. This allows you to set CSS for messages on a per-service basis. For example, you can have 1 colour theme assigned to Beam messages, and another to Twitch messages. The `[data-platform]` tag is currently only used on the chat messages, so this is a very specific tag. We will be following the same example as above.

Now, remember that `!important` tag we talked about no less than a couple of minutes ago? We need that now. The background colour for the chat messages is set inline, therefore we need the `!important` tag to make sure our CSS is the style that is applied.

There are currently 3 chat services support by StreamJar. Beam, Twitch and Hitbox. Each of these can be accessed using the `[data-platform]` tag. Here is what you need:

* Beam - `[data-platform='beam']`
* Twitch - `[data-platform='twitch']`
* Hitbox - `[data-platform='hitbox']`

So as an example, we can now change the background colour of messages for each service. This is accomplished by using the example above, and adding the `[data-platform]` tag to the element we are changing:

```css
	.overlay .canvas .element[data-type='chat'] > .chat > .messages > div[data-platform='beam'] {
		background-color: rgb(0, 255, 255) !important;
	}
	
	.overlay .canvas .element[data-type='chat'] > .chat > .messages > div[data-platform='twitch'] {
		background-color: rgb(255, 0, 255) !important;
	}
```

<img src="https://raw.githubusercontent.com/iamomicron/StreamJarCSS/master/images/chatBefore.png" alt="before" </img>

We now have a cyan background for Beam messages, and a magenta background for Twitch messages. But, seeing as our text is white we cannot see the messages very clearly. The sender's name, the message and the icon colours can also be changed. To do this, just access the `.name`, `.msg` and `.icon`. Here's an example:

```css
	.overlay .canvas .element[data-type='chat'] > .chat > .messages > div[data-platform='twitch'] .name,
	.overlay .canvas .element[data-type='chat'] > .chat > .messages > div[data-platform='twitch'] .msg,
	.overlay .canvas .element[data-type='chat'] > .chat > .messages > div[data-platform='twitch'] .icon {
		color: #000000; /* Black text */
	}
```

And here's what we have after setting all 3 to black.

<img src="https://raw.githubusercontent.com/iamomicron/StreamJarCSS/master/images/chatAfter.png" alt="after"</img>

***

Other Examples
--------------

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
	
	From this:
	
	<img src="https://raw.githubusercontent.com/iamomicron/StreamJarCSS/master/images/notiBefore.png" alt="before" </img>
	
	to this:
	
	<img src="https://raw.githubusercontent.com/iamomicron/StreamJarCSS/master/images/notiAfter.png" alt="after"</img>

For more examples, please visit: https://github.com/iamomicron/StreamJarCSS/blob/master/examples.css
