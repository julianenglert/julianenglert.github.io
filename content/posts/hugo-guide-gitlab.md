+++
author = "Julian Englert"
title = "Hugo guide for GitLab"
date = "2020-11-06"
description = "Build a Hugo website and deploy it on GitLab"
draft = "true"
tags = [
"guide",
"Hugo",
"GitLab",
"Git",
]
+++

Build a Hugo website and deploy it on GitLab

(*also see my [earlier guide](/hugo-guide-netlify) for deploying on Netlify*)


### Installation
- [install Chocolatey using PowerShell](https://chocolatey.org/install) (open as admin)  <!--more-->
- [install Hugo via Chocolatey](https://gohugo.io/getting-started/installing/#chocolatey-windows) still using PowerShell 
- [install Git via Chocolatey](https://chocolatey.org/packages/git)

### Create Hugo site and download theme
- create new website running `hugo new site website` which creates the root folder for the site  (`~/website`)
- download a theme with `git clone https://theme-url` into `/themes/theme`

### Add content and test locally
- modify `config.toml` and `.md`  files in website directory
- run `hugo server` in root directory
- see locally hosted website according to changes

### [Host website on GitLab](https://gohugo.io/hosting-and-deployment/hosting-on-gitlab/)
- add `.gitlab-ci.yml` file containing [^hosting-on-gitlab]
```

image: monachus/hugo

variables:
  GIT_SUBMODULE_STRATEGY: recursive

pages:
  script:
  - hugo
  artifacts:
    paths:
    - public
  only:
  - master
```

- add `.gitsubmodules` file containing [^add-git-submodule]
```
[submodule "themes/theme"] 
  path = themes/theme 
  url = https://theme-url.git
```
 - create GitLab repository named *user.gitlab.io*
 - push local website folder to this repository
	 - `git remote add origin https://gitlab.com/user/user.gitlab.io.git`
	 - `git add .`
	 - `git commit -m "comments"`
	 - `git push -u origin master`
- wait for website to build 
	- see `https://gitlab.com/user/user.gitlab.io/pipelines`
	- when done, access at `https://user.gitlab.io`
- set repository to **Public** if not already by accessing `https://gitlab.com/user/user.gitlab.io/edit`

## How to modify theme layouts

Copy the `.html` layouts from the theme's `layouts` folder to your website's root directory (there should be an empty `layouts` folder there - if not, create it)

Whatever changes you now make to the `.html` layouts in the root folder will change the structure of your website. **Hugo will use these layouts over the ones in `/themes/<your theme>/layouts`.** 

Make sure to check that you didn't break the site by running `hugo server` before pushing to your hosting server.
