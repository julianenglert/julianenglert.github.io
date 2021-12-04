+++
author = "Julian Englert"
title = "How to Use Daily Notes in Obsidian"
date = "2020-09-21"
description = "Process information, plan & execute tasks during the day, and keep track of content and recommendations"
tags = [
    "guide",
    "Obsidian",
    "productivity",
    "notetaking",
]
+++


**[Obsidian](https://obsidian.md)** is a powerful knowledge management tool that allows you to take notes in a networked fashion. 

The ability to form **`[[connections]]`** between them mimics the way ideas are captured in your brain, with the distinction that Obsidian never forgets: Built on top of a local folder of Markdown files, it is the perfect tool to construct a "second brain".

In this series I'll show some of the workflows I've found to be working well with Obsidian.

Here: **Daily notes with capture note**

<!--more-->

## Purpose
- process incoming information (thoughts, ideas, recommendations)
- write down tasks for the day and hold yourself accountable to them
- keep track of content you consume and serve as springboard for notes taken on podcasts, articles, etc

## Main

The **`000 Capture`**[^000] note is at the heart of my day to day note-taking in Obsidian. 

![](/obsidian_daily_notes/capture_desktop.png)

It's the universal list of all tasks and todos, collects reading / podcast / Netflix recommendations and serves as a shopping list.

In it I plan out my day and develop thoughts into notes. 

I use it to keep track of all the things I'm doing through out the day (writing emails, planning things, writing or documenting code, talking to people etc.). 

Markdown allows you to create checkbox lists with nested items so finished tasks can simply be crossed out.

For meetings, I create a note with discussion topics or minutes directly from the capture note.

 I create a note for each article I read during the day with some basic metadata with author information, date of publishing and reading, link and tags. This allows organizing my collection of notes via tags and MOCs (*maps of concepts*).
 
![](/obsidian_daily_notes/reading_notes.png)
 
Using one of the various Markdown editors for iOS, I can add thoughts, tasks, and recommendations to my capture note on mobile too[^icloud].

![](/obsidian_daily_notes/capture_mobile.png)

At the end of the day, I copy all completed tasks, readings and meeting notes of the day into the corresponding daily note. 

![](/obsidian_daily_notes/daily_note.png)

Over time, the daily notes thus become a repository that keeps track of tasks, projects and content consumed.

Unfinished tasks stay in the capture note. There, after doing my daily planning and prioritization on the next day I either pick them up or discard them.  

On the top of my daily notes you can see a section with links to yesterday's and tomorrow's note. This allows me to quickly navigate between daily notes to revisit them or to move tasks from one day to the next.

![](/obsidian_daily_notes/daily_note_header.png)

The Markdown for this header template can just be copied from one daily note to another and adjusted for each day or you can use a script to paste it with a shortcut of your choice (here with [Autohokey](https://autohotkey.com/)[^autohotkey])

```md
<< Yesterday `[[link to yesterday's daily note]]` | `[[link to tomorrows's daily note]]` Tomorrow >>


`[[link to capture note]]`

---

your notes

```



[^000]: the **`000`** in the file name ensures that the note is always on top in the file explorer pane

[^icloud]: this requires using iCloud as directory for the Obsidian Vault 

[^autohotkey]:
	```ahk
	; Syntax
	; ^ = CTRL
	; ! = ALT
	; + = SHIFT
	; # = WIN
	; :: = run when pressed keys together

	^+d::
		yesterday := a_now
		yesterday += -1, days

		tomorrow := a_now
		tomorrow += 1, days

		FormatTime, tomorrow, %tomorrow%, yyyy-MM-dd
		FormatTime, yesterday, %yesterday%, yyyy-MM-dd

		SendInput, << Yesterday **[[Daily notes/%yesterday% | %yesterday%]]**{space}|{space}**[[Daily notes/%tomorrow% | %tomorrow%]]** Tomorrow >> 
		Send, {Enter}
		Send, {Enter}
		SendInput, **[[000 Capture]]**
		Send, {Enter}
		Send, {Enter}---
		Send, {Enter}
	Return

	```
