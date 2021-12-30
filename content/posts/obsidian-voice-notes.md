+++
author = "Julian Englert"
title = "iOS shortcut to record voice memos and transcribe them to Obsidian"
date = "2021-12-31"
draft = "true"
+++

>This workflow allows you to hold the lock button off your iPhone, say "dictate" and then dictate a note with the transcribed text being directly linked to your obsidian daily note. In fact these sentences were dictated using this shortcut :)

![[obsidian.PNG]]

### Setup
- Create new Shortcut in iOS with building blocks
	- *Dictate Text*
	- *Append to File* 
		- save *Dictated Text* to file path *Current Date* 
	- *Text*
		- leave empty 
	- *Append to File* 
		- save *Text* to same file path (*Current Date*) as before [^append]
- Go to settings and change Siri settings to trigger on side button

|![[shortcuts.PNG]]| ![[siri.PNG]]| 
|----|----|



- On your Mac/Windows, go to the iCloud folder where Shortcuts saves file
	- located in `/Users/User/Library/Mobile\ Documents/iCloud~is~workflow~my~workflows/Documents/`
- Symlink this folder into your Obsidian Vault
	- open terminal and run `ln -s <path to of your Obsidian vault>`
- Install the plugin [txt as md](https://github.com/deathau/txt-as-md-obsidian) to open `.txt` files directly in Obsidian [^txtasmd]
- Create a template that directly links the text file with transcribed notes to your daily note for a given day
	- e.g. using [Templater](https://github.com/SilentVoid13/Templater) I include this line in my daily note template: `[[Documents/Memos/<% tp.date.now() %>.txt]]]]`




[^append]: This way, triggering the shortcut for the first time on a given day will create a new txt file with the transcribed text. For all subsequent recordings on the same day however, the transcribed text will directly be appended to the already existing file. Appending the empty *Text* will create a new line after every transcribed block

[^txtasmd]: I didn't figure out how to make the iOS shortcut save the transcribed text as markdown. There's an option to save as rich text but the resulting file was still .txt for me. There's another shortcut building block called "Convert rich text to markdown" but applying it afterwards didn't help, instead, it just yielded a .txt with a markdown image link in it -.-