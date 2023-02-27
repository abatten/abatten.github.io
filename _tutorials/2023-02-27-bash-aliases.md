---
layout: page-fullwidth
title: "Some Useful Bash Aliases"
subheadline: "Bash | Terminal"
meta_teaser: "A collection of some useful Bash aliases."
teaser: "A collection of some useful Bash aliases."
header:
    image_fullwidth: "coding-header.jpg"
    title: ' '
    background-color: "#777777"
    caption: ' '
    caption_url: ' '
image:
    thumb:  tutorials/bash/bash_icon.png
    homepage: tutorials/bash/bash_icon.png
    caption: ' '
    caption_url: ' ' 
categories:
    - tutorial
post_date: 2023-02-27
modify_date: 2023-02-28

permalink           : "/tutorials/useful_bash_aliases/"
---

<div class="row">
<div class="medium-4 medium-push-8 columns" markdown="1">
<div class="panel radius" markdown="1">
**Table of Contents**
{: #toc }
*  TOC
{:toc}
</div>
</div><!-- /.medium-4.columns -->

<div class="medium-8 medium-pull-4 columns" markdown="1">

I have collected a few interesting bash aliases that I use in my day-to-day programming.
This tutorial is a list of the ones that I have found most useful. I will note that a few
of these aliases are MacOS specific, but I am sure you could find the Linux equivalent somewhere
one the internet.

I put all of these bash aliases in a `.bash_aliases` in my home directory and load them by including the following in my `.bashrc` file:
```bash
# Add bash aliases
if [ -f ~/.bash_aliases ]; then
    source ~/.bash_aliases
fi
```
This checks to see if the `.bash_aliases` file exists, and if it does, load all of the aliases. 

## Additional `ls` options.
```bash
alias ls="ls -h"                       #  Use human readable filesizes
alias la="ls -hA"                      #  Show hidden files easier
alias lla="ls -hlA"                    #  Show long hidden files
```
I use `ls -lA` to show to list the details of all the hidden files so often
that I found it useful to just have it as an alias. 

I additionally always want to use `-h` to make all the file sizes in human readable format.
It just makes it much easier to see how many kB/MB/GB all my files are.

## Faster backwards `cd`.
```bash
alias ..="cd .."
alias ...="cd ../.."
alias ....="cd ../../.."
alias .....="cd ../../../.."
alias -- -="cd -"
```
To go backwards from a directory (`cd ..`) I can just use `..`. Or I use `...` to go
backwards two directories, etc

Also, I can use `-` to switch between the last two directoties that I was in.
Useful when I need to swap between two entirely different directories quickly a few times.

## Open the current terminal directory in Finder.
```bash
alias f="open -a Finder ./"
```
Quite often I want to open whatever directory I am in with Finder. This is usually
so I can look at all of the thumbnails of images quickly reather than opening files from
the terminal. So by just typing `f` I open up Finder 'here'.

## Refresh bash session in same directory
```bash
alias restart="source ~/.bash_profile"         #  Quickly refresh shell
```
I use `restart` to quickly refresh the bash shell without having to close then open
a new terminal. I usually use this after I've edited my `.bashrc`, `.bash_profile` or `.bash_aliases` file.

## Hide/Show all Desktop Icons.
```bash
alias hidedesktop="defaults write com.apple.finder CreateDesktop -bool false; killall Finder;"
alias showdesktop="defaults write com.apple.finder CreateDesktop -bool true; killall Finder;"
```
These are useful for when I have a presentation and I don't want everyone
to know how messy my desktop is. I just type `hidedesktop` in the terminal,
and all of my icons disappear. (THe files are still there but they dont render
the icon itself. If I want to bring them back I just type `showdesktop`.

## Count the number of files in all sub directories
```bash
alias count='find . -type f | wc -l'           #  Count files
```
I use this whenever I need to know how many files there are in my current dirrectory. Note that this also includes hidden files, but doesn't include directories themselves.
So if you have directory that contains two directories, one containing 2 files and another with 3 files, `count` will return 5. 

## Get IP Address and External IP Adress
```bash
alias ip="ipconfig getifaddr en0"
alias ipext="curl -s http://checkip.dyndns.org/ | grep -o '[0-9][0-9]*.[0-9][0-9]*.[0-9][0-9]*.[0-9]*'"
```
Sometimes I need to find my current IP address, and instead of googling "What is my IP address?" every time, 
I use `ip` and `ipext` to find my internal and external IP addresses.

Your "internal IP address" is the IP address you use on your local, internal network (i.e. LAN).
Your "external IP address" is the IP address you use when communicating to other machines on the internet. 
This is assigned by your internet service provider.

### All of the aliases from this tutorial
```bash
alias ls="ls -h"                       #  Use human readable filesizes
alias la="ls -hA"                      #  Show hidden files easier
alias lla="ls -hlA"                    #  Show long hidden files

alias ..="cd .."
alias ...="cd ../.."
alias ....="cd ../../.."
alias .....="cd ../../../.."     
alias -- -="cd -"                      # Switch to previous directory

alias f="open -a Finder ./"            #  Open current directory in Finder

alias restart="source ~/.bash_profile"         #  Quickly refresh shell

alias count='find . -type f | wc -l'           #  Count files

# Get IP Addresses
alias ip="ipconfig getifaddr en0"
alias ipext="curl -s http://checkip.dyndns.org/ | grep -o '[0-9][0-9]*.[0-9][0-9]*.[0-9][0-9]*.[0-9]*'"

# Hide/Show all the desktop icons
alias hidedesktop="defaults write com.apple.finder CreateDesktop -bool false; killall Finder;"
alias showdesktop="defaults write com.apple.finder CreateDesktop -bool true; killall Finder;"

```

