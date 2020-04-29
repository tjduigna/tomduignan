---
title: "self.blog"
date: 2020-04-28T10:33:41+09:00
description: "Notes from setting up this site"
draft: false
hideToc: false
enableToc: true
enableTocContent: false
author: td
tags:
- hugo
- aws
- amplify
series:
-
categories:
- hugo
image: images/blog-zero/pc-power-button-logo-clipart.png
---

## Simply Static Site

So I finally got my act together enough to put up a website.  Initially struck by a barren beautifulhugo gitlab pages site, it seemed there was a fun weekend project in ironing out the details of choosing a theme and setting up hosting and deployment.  Hugo was as good a choice as any for a static site generator framework and AWS is very simple with amplify serverless hosting.  The project was initialized using the hugo command line utility by following the tutorial and updates to the project are tracked in git.

### Choices

The theme I chose can be found at [https://github.com/zzossig/hugo-theme-zzo](https://github.com/zzossig/hugo-theme-zzo).  It is a fantastic theme that allows for a lot of customization out-of-the-box.  I did have to follow some instructions but the `README.md` is quite extensive.  After figuring out the theme, it was time to log in to AWS. Registering a domain is easy with Route53 and setting up an amplify project attached to a git repository was as simple as following the prompts. As easy as amplify is to use (it auto-detects the hugo project), the default version of hugo in its pipeline is not sufficient for my must-have theme. After attempting to follow the prescription outlined here [https://gohugo.io/hosting-and-deployment/hosting-on-aws-amplify/](https://gohugo.io/hosting-and-deployment/hosting-on-aws-amplify/) to no avail, I had to be explicit by adding the following lines to my `amplify.yml` file from AWS:
``` yml
    build:
      commands:
        - wget https://github.com/gohugoio/hugo/releases/download/v0.69.0/hugo_extended_0.69.0_Linux-64bit.tar.gz
        - tar -xf hugo_extended_0.69.0_Linux-64bit.tar.gz
        - mv hugo /usr/bin/hugo
        - rm -rf hugo_extended_0.69.0_Linux-64bit.tar.gz
        - hugo
```
Nice. The deployment pipeline is set up so commits to my master branch deploy directly to my hosted domain name. Everything works and was fairly simple to set up. The only problem left is generating content...


### Futures

I'm attracted to the overall simplicity of this setup and will be hard-pressed to find a more maintainable project. Unfortunately that same simplicity leaves me torn, as it is not the cutting edge front-end user experience that has become so "important" recently. It sounds like a fun challenge to try, for example, embedding react components into the site, but my guess is that this would be more of a headache than it is worth. Ultimately pragmatism wins out and content gets published. Insightful technical notes are for naught if left to bit rot on hard disk drives unplugged and forgotten. Anyway, here's some python syntax highlighting:
``` python
try:
    int(bool('a')) == 'a'
except Exception as e:
    pass
print("Hello, world!")
```

