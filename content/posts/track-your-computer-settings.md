---
title: Create a Repo to Track Your Computer's Settings
date: 2020-02-17T21:14:31-04:00
tags: [git]
categories: [tech doc]
draft: false
---

As a beginner, I manually add several dotfiles to the Repo like this.

```bash
# Create a Repo
git clone git@github.com:<username>/dotfiles.git
cd dotfiles
mv ~/.vimrc .
git add .vimrc
git commit -m "your message"
 
# Symbolically linking files
ln -s /path/to/dotfiles/.vimrc ~/.vimrc
 
# push to remote
git push origin master
```

References:
Some tutorials : [Guide to dotfiles on Github](https://dotfiles.github.io/)
