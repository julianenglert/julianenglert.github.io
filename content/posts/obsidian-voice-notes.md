+++
author = "Julian Englert"
title = "iOS shortcut to record voice memos and transcribe them to Obsidian"
date = "2021-12-31"
draft = "false"
+++

>This workflow allows you to hold the lock button off your iPhone, say "dictate" and then dictate a note with the transcribed text being directly linked to your obsidian daily note. In fact these sentences were dictated using this shortcut :)

![](/obsidian-voice-notes/obsidian.PNG)

### Setup
- Create new iOS Shortcut (or copy mine [here](https://www.icloud.com/shortcuts/9c48536a66ec4ab4b1e9192f06e2a632))
	- *Dictate Text*
	- *Text*
		- one new line 
	- *Append to File* 
		- Append "**Dictated text** `space` **Text**" to file path *Current Date* [^append]
- Go to settings and change Siri settings to trigger on side button

|![](/obsidian-voice-notes/shortcuts.PNG)| ![](/obsidian-voice-notes/siri.PNG)| 
|----|----|



- On your Mac/Windows, go to the iCloud folder where Shortcuts saves files
	- located in `/Users/<username>/Library/Mobile\ Documents/iCloud~is~workflow~my~workflows/Documents/`
- Symlink this folder into your Obsidian Vault
	- open terminal and run `ln -s <path to of your Obsidian vault>`
- Install the plugin [txt as md](https://github.com/deathau/txt-as-md-obsidian) to open `.txt` files directly in Obsidian [^txtasmd]
- Create a template that directly links the text file with transcribed notes to your daily note for a given day
	- e.g. using [Templater](https://github.com/SilentVoid13/Templater) I include this line in my daily note template: `[[Documents/Memos/<% tp.date.now() %>.txt]]]]`




[^append]: Using *Append to file* instead of *Save to file* prevents creating new files for each recording. Triggering the shortcut for the first time on a given day will still create a new txt file with the transcribed text but for all subsequent recordings on the same day, the transcribed text will be appended to the already existing file. Appending *Dictated Text* **and** *Text* (with a new line in it) will create a new line after every transcribed block.

[^txtasmd]: I didn't figure out how to make the iOS shortcut save the transcribed text as markdown. There's an option to save as rich text but the resulting file was still .txt for me. There's another shortcut building block called "Convert rich text to markdown" but applying it afterwards didn't help, instead, it just yielded a .txt with a markdown image link in it -.-