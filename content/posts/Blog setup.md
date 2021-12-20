+++
author = "Julian Englert"
title = "Blog setup"
date = "2021-12-04"
description = "Description"
+++

## Installation
- install git
- install hugo

## Set up repo for Github Page
- follow these instructions: https://pages.github.com/

## Create Hugo site and download theme
- create new website running `hugo new site website` which creates the root folder for the site  (`~/website`)
- download a theme with `git clone https://theme-url` into `/themes/theme`

## Add content and test locally
- modify `config.toml` and `.md`  files in website directory
- run `hugo server` in root directory
- see locally hosted website at localhost:1313

## How to modify theme layouts
- copy the `.html` layouts from the theme's `layouts` folder to your website's root directory (there should be an empty `layouts` folder there - if not, create it)
- changes to the `.html` layouts in the root folder will now change the structure of your website --> **Hugo will use these layouts over the ones in `/themes/<your theme>/layouts`.** 
- make sure to check that you didn't break the site by running `hugo server` 

## Set up Github Actions to automatically build Hugo website
- Follow these instructions: https://sgibson91.github.io/blogging-with-hugo-and-github-pages/04-continuous-deployment/index.html

## Git commands
- `git add .`
- `git commit -m "comment"`
- `git push origin main`

## Set up Obsidian integration
- create *symlink* in your Obsidian Vault pointing to the website folder
- access your blog posts, about me page etc directly in your Obsidian Vault 
