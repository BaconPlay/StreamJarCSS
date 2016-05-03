StreamJar Custom CSS
====================

List and exaples produced by Rob Aimes (IAmOmicron)
- http://aimes.eu


**This is NOT an official release or product of StreamJar!**

*Use this with caution. This is provided as an example and should only be taken as such.
I am not responsible for your CSS. Broken overlays are your own doing!*

This document gives some information on how to edit the StreamJar overlay elements with CSS
Some examples are provided for convinience.

A basic understanding of CSS is assumed.

Documentation:
	The CSS created should be used in the OBS Browser Window Settings.
	
	[data-type]
	===========
	To access an element a specific 'path' is followed. This path is similar for all overlay elements.
	Where you encounter [data-type='dataType'] the 'dataType' in quotes, should be replaced with one of
	the valid types listed below.
	
	Valid types: 'song' | 'notification' | 'goal' | 'chat' | 'banner' | 'images' | 'trigger' | 'text'
	
	
	
	[data-id]
	=========
	Since all of the elements are classes, if you have multiple elements of the same type on a single
	overlay, they will all be changed unless given the [data-id] tag as well.
	
	To change a specific element siple add the [data-id] tag after the [data-type] tag. NO SPACE! For example:
		[data-type='dataType'][data-id='dataID']
		
	The data-id for an element can be gained using the Google Chrome console. Simply open the console with F12
