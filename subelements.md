*The incomplete list of how to access certain sub elements for each data type in the StreamJar overlay.*
--------------------------------------------------------------------------------------------------------

**NOTES:**
* **Some of these classes may be wrong**
* **Any of these can change or break over time as this is unofficial**
* **This is just a list of classes**
* **Some classes require access to the parent `> div` first. It is not explicitly stated which classes need this**
* **Please refer to the StreamJar overlay CSS source file for accuracy if you are unsure**


***************************


* **Goal**
	* `.bar`
	* `.bar .progress`
	* `.data`
	* `.data .percentage`
	* `h3`
	
* **Song**
	* `.image`
	* `.videoplayer`
	* `.videoplayer > video`
	* `h2`
	* `h3`
	* `> div.name`
	* `> div.artist`
	* `.source`

* **Chat**
	* `> .chat`
	* `> .chat > .messages`
	* `> .chat > .messages > div`
	* `> .chat > .messages > div .name`
	* `> .chat > .messages > div .msg`
	* `> .chat > .messages > div .icon`
	
* **Chat Services - [data-platform]**
	* `> .chat > .messages > div[data-platform='beam']`
		* `> .chat > .messages > div[data-platform='beam'] .name`
		* `> .chat > .messages > div[data-platform='beam'] .msg`
		* `> .chat > .messages > div[data-platform='beam'] .icon`
	* `> .chat > .messages > div[data-platform='twitch']`
		* `> .chat > .messages > div[data-platform='twitch'] .name`
		* `> .chat > .messages > div[data-platform='twitch'] .msg`
		* `> .chat > .messages > div[data-platform='twitch'] .icon`
	* `> .chat > .messages > div[data-platform='hitbox']`
		* `> .chat > .messages > div[data-platform='hitbox'] .name`
		* `> .chat > .messages > div[data-platform='hitbox'] .msg`
		* `> .chat > .messages > div[data-platform='hitbox'] .icon`

* **Notification**
	* `.image`
	* `.videoplayer`
	* `.videoplayer > video`
	* `h2`
	* `h3`
	* 
* **Banner**
	* `.title`
	* `.inner`
	* `.inner div`
	* `.inner span`
	* `.inner .avatar`
	* `.inner .none`
		

**********

**The following elements need further looking into and, as far as I am aware, cannot be changed through CSS as of yet**

* **Text**
* **Images**
* **Trigger**

**********

**Final warning: This *is* incomplete and if and when StreamJar updates, anything can stop working**
