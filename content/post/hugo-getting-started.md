---
title: "Hugo: Getting Started"
date: 2018-06-08T19:38:22-06:00
draft: false
---

## Introduction

I have decided that I need to have a new website that is simple, clean, and effective. In my mind I had decided I would start writing a pure HTML page then learn some CSS and finally add some javascript but I quickly realized that while the thought of a pure HTML page sounds pretty cool and nostalgic, from a perspective of learning I would be better off starting somewhere else. I immediatley thought about the last tool that I used for web design NVU which was apparently discontinued in 2005 (wow I'm old). During all of my searching I found a project that will do exactly what I want.

Hugo, a static website generator. Hugo can work with just about any modern web technology and ,most importantly, be used to create static webpages.

From the [Hugo](https://gohugo.io/) website:

> Hugo is one of the most popular open-source static site generators. With its amazing speed and flexibility, Hugo makes building websites fun again.

I have to say that I agree Hugo is definetly fun. The program is deceptively powerful. It takes only a couple of minutes to get setup and I was able to get the basics figured out in about 20 minutes thanks to the excellent [Quick Start](https://gohugo.io/getting-started/quick-start/) tutorial.

## Starting your first site

Working with Hugo is pretty simple but only if you are familiar with the command line. I would definetly recommend you follow the quick start linked above before you attemp this. I decided I would use git and github to help me keep track of my website. 

```
sudo snap install hugo
hugo new site sitename
cd sitname
git init
```
Then I just needed to add a theme because what good is a plain old boring site when you have access to a world of easily installed themes. I went to https://themes.gohugo.io/ and found a theme that I liked ([Minimal](https://themes.gohugo.io/minimal/)) and ran the following commands.

```
git add submodule https://$ git submodule add https://github.com/calintat/minimal.git themes/minimal
git submodule init
git submodule update
cp themes/minimal/exampleSite/* . -r
git add --all
git commit -m "initial commit with example site"
git remote add origin https://github.com/your_username/repository_name.git
git push -u origin master
```

These commands installed the theme as a submodule to my git project updated and then copied the "exampleSite" folder in its entirety over the top of my blank site project. I find this useful because you can fiddle with the content that is included in the example site and decide what you like and what you don't. Once you have everything ready to go just simple remove any of the files that you don't want and add you own posts.

```
hugo new post/postname.md
vim content/post/postname.md

## enter your content making sure to set "draft = false" in the metadata header of your postname.md file.

hugo server
```

The above command will run your site in the Hugo test server making it available on localhost:1313.

## Building and deploying your site

Now that you have created your site it is easy to create the files required to push to your site and make it live. Now is a goodtime to push your changes to your github if you are using that as well.

```
## first build the site
hugo

## push to github
git add --all
git commit -m "first post"
git push -u origin master
```

Now you just need to take the contents of the public directory and upload it to your webserver and everything should be ready to go.
