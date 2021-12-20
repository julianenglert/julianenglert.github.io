+++
author = "Julian Englert"
title = "Hugo guide Netlify"
date = "2020-08-24"
description = "Tutorial for how to create static website and deploy with Netlify"
draft = "true"
tags = [
    "markdown",
    "Hugo",
    "Netlify",
    "Git",
]
+++

This article shows how create a static website with Hugo on your local machine, push it to GitHub and deploy it via Netlify.
<!--more-->

**Steps** (all on Windows 10)

Recommended tools:
- Sublime Text (https://www.sublimetext.com/)
- PowerToys for Markdown preview in Windows Explorer (https://github.com/microsoft/PowerToys)

Install Chocolatey using PowerShell (open as admin) (https://chocolatey.org/install)

Install Hugo via Chocolatey still using PowerShell (https://gohugo.io/getting-started/installing/#chocolatey-windows)

Install Git via Chocolatey (https://chocolatey.org/packages/git)

Use terminal commands (https://www.techrepublic.com/article/16-terminal-commands-every-user-should-know/) to navigate to directory for new test site (doesn't really matter where, just so you can find it in the file explorer again)

Follow Hugo Quick Start Guide (https://gohugo.io/getting-started/quick-start/#step-2-create-a-new-site) using a theme of your choice

If you get an error along the lines of "bare keys cannot contain '\x00'", open the *config.toml* using a text editor and fix the line that is supposed to say `theme = "theme_of_your_choice"`. If the file contains lots of `3a2f 2f6a 756c 6961 6e2d 656e 676c 6572` or similar, it's hexadecimal and you have to reopen with UTF encoding.

Use the file explorer to move some of the *exampleSite* content into your actual website directory and play in *config.toml* with the parameters (website title, categories, date format etc) to get a better feel for how things work

Create a new GitHub repository in your web browser

Use the Git Bash command line to push the local website directory to GitHub (https://www.youtube.com/watch?v=ibNqauPoicg)

Use Netlify (https://www.netlify.com/) to connect to your GitHub account, select the repository with the website and deploy it