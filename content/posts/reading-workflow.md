+++
author = "Julian Englert"
title = "My Reading Workflow"
date = "2020-08-26"
description = "How to read a book and never forget its contents"
tags = [
    "guide",
    "Python",
    "Obsidian",
    "reading",
]
+++

This post shows how to build a reading workflow that allows you to extract summaries from books you've read to further work with the ideas in them. 
<!--more-->

# Goal
Be able to read any book digitally and process its most important ideas to never forget them

![overviewm](/reading_workflow/overviewm.png)

# Steps
1. Create a personal library of epubs
2. Read epubs on mobile devices
3. Take highlights while reading to construct a summary of the book
4. Import highlights into knowledge management system
5. Work with the summarized books and connect ideas

# Step by Step

## Import epubs into [Calibre](https://calibre-ebook.com/)
- set library path to local machine or cloud drive
- Calibre can download cover, metadata, abstract etc for book
- epub will be saved in library in standardized folder-file format

## Upload epub to [PlayBooks](https://play.google.com/books) for reading
- in the mobile app in *Settings* -> *Google Drive sync* toggle *Save your notes, highlights and bookmarks* (enables it for mobile app and web app)
- while reading, highlight parts, chapters (and subchapters if meaningful) as well as text excerpts[^figures] 
- highlights get compiled into a Google Doc that gets saved to your Drive under *PlayBook Notes*

![g1](/reading_workflow/g1.PNG)
## Clean up highlights with this [Google Colab Python script](https://colab.research.google.com/drive/1J11DJ6Bu1wRODx-XJs194aoRW3FIyO7z?usp=sharing)
Copy file ID from Google Document 
![g2](/reading_workflow/g2.PNG)

Run the script with your file ID to get extracted text file 
![g3](/reading_workflow/g3.PNG)

## Import into note-taking / knowledge management (here shown using [Obsidian](https://obsidian.md))

Paste raw text  
![o1](/reading_workflow/o1.PNG)


Recreate headings and insert images / figures. Re-highlight the summary to create an even more condensed version for fast re-reading. Optionally, write some metadata 

![o2m](/reading_workflow/o2m.png)
![o3m](/reading_workflow/o3m.png)

## Example of an interconnected book

Josh Kaufman - The Personal MBA

![pmba](/reading_workflow/pmba.jpg)


[^figures]: In PlayBooks, there is no way to highlight images and figures directly. Make sure to highlight the caption (<mark>Figure 3.1: This graph shows XYZ...</mark>) if there is one, to find where to insert the missing figure later in your knowledge management system
