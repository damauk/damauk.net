---
title: "Hugo: Getting Started"
date: 2018-06-08
tags: ["hugo", "linux"]
draft: false
---
## Introduction

I have decided that I need to have a new website that is simple, clean, and effective, replacing the slow, out of date WordPress blog I had before. I was thinking I would start writing a pure HTML page then learn some CSS and finally add some javascript, but I quickly realized that beyond being extremely nostalgic, pure HTML websites are a thing of the past and I would be better off starting somewhere else. I immediately thought about the last tool that I used for web design NVU which I have discovered was discontinued in 2005 (wow I'm old). I never learned much HTML coding, so I always used a GUI based IDE, but it appears most of the programs that were WYSIWYG editors have pretty much disappeared, replaced by online website builders that force you to use one company or another's hosting services.

During my search for a replacement to my old favorite NVU I came across static website generators. My favorite has got to be Hugo. Hugo can work with just about any modern web technology. Hugo uses simple folder structures and markdown formatted content to create websites. You write your .md files in the appropriate folders and render the site using the command "hugo." To help understand what Hugo is I have included the description from the [Hugo](https://gohugo.io/) website:

> Hugo is one of the most popular open-source static site generators. With its amazing speed and flexibility, Hugo makes building websites fun again.

I have to say that I agree Hugo is fun. The program is deceptively powerful. It takes only a couple of minutes to setup, and I was able to get the basics figured out in about 20 minutes thanks to the excellent [Quick Start](https://gohugo.io/getting-started/quick-start/) tutorial.

## Starting your first site

Working with Hugo is pretty simple but only if you are familiar with the command line. I would recommend you follow the quick start linked above before you attempt this. I decided I would use git and Github to help me keep track of my website. 

```
sudo snap install hugo
hugo new site sitename
cd sitename
git init
```
Then I just needed to add a theme because what good is a plain old boring site when you have access to a world of easily installed themes. I went to https://themes.gohugo.io/ and found a theme that I liked ([Minimal](https://themes.gohugo.io/minimal/)) and ran the following commands.

```
git add submodule https://github.com/calintat/minimal.git themes/minimal
git submodule init
git submodule update
cp themes/minimal/exampleSite/* . -r
git add --all
git commit -m "initial commit with example site"
git remote add origin https://github.com/your_username/repository_name.git
git push -u origin master
```

These commands installed the theme as a submodule to my git project updated and then copied the "exampleSite" folder in its entirety over the top of my new site project. I find this useful because you can fiddle with the content that is included in the example site and decide what you like and what you don't. Once you have everything ready to go just pure remove any of the files that you don't want and add your posts.

```
hugo new post/postname.md
vim content/post/postname.md

## enter your content making sure to set "draft = false" in the metadata header of your postname.md file.

hugo server
```

The above commands create a new file under the "posts" menu and runs your site on the Hugo test server making it available on localhost:1313.

## Building and deploying your site

Now that you have created your site it is easy to create the files required to push to your site and make it live. Now is an excellent time to push your changes to your Github if you are using that as well.

```
## first build the site
hugo

## push to github
git add --all
git commit -m "first post"
git push -u origin master
```

Now you need to take the contents of the public directory and upload it to your, and everything should be ready to go. I am currently manually uploading the contents of my public/ directory to my web server, but I plan on implementing a rysnc over ssh to increase performance for site deployment.