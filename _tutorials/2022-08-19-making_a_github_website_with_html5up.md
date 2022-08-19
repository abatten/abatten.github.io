---
layout: page-fullwidth
title: "Creating a Website with Github and HTML5up"
subheadline: "Github | HTML5up"
meta_teaser: "The basics of setting up a static website for free using Github pages and html templates from HTML5up."
teaser: "The basics of setting up a static website for free using Github pages and html templates from HTML5up."
header:
    image: github_html5up.png
    background-color: "#d97a73"
    caption: ' '
    caption_url: ' '
image:
    thumb:  github_html5up.png
    homepage: github_html5up.png 
    caption: ' '
    caption_url: ' ' 
categories:
    - tutorial
post_date: 2022-08-19
modify_date: 2022-08-19

permalink           : "/tutorials/creating_a_website_with_github_and_html5up/"
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

This tutorial is a summary of the *Cookies 'n' Code* tutorial that I run every year at the 
[Centre of Astrophysics and Supercomputing (CAS)](https://astronomy.swin.edu.au/) at the [Swinburne University of Technology](https://www.swinburne.edu.au/).
The purpose of this tutorial was to get each of the PhD students to have a basic academic landing page that they can use to promote their work.

*Cookies 'n' Code'* is a weekly coding group meeting at CAS, where people get together to discuss code and teach each other new things.


## Step 0: Creating a Github Account
This one is pretty obvious -- Go to [https://github.com/](https://github.com) and create and account. 

We will be using a feature of Github called *Github Pages*. Github Pages, lets you turn a Github repository into a website provided you give it the right name.

## Step 1: Create Github Repository
Create an empty repository on Github with the name ``<USERNAME>.github.io``.

For example, if your username is `jsmith`, then you create a repository called ``jsmith.github.io``

It is vital to make sure that the name of the repository fits exactly this format and that it is *public*, otherwise Github wont turn your repository into a website. 
The name of this repository will also be the url to the website. i.e. https://jsmith.github.io.

## Step 2: Find a website template
You could write your own html and css if you like. But there are plenty of templates out there so you don't have to. My favourites are from [https://html5up.net/](https://html5up.net).

Check out: Prologue, Editorial, Strata, Phantom, Strongly Typed, Escape Velocity. They might be some good starting point, but really anyone of them are good.

HTML5up websites also have the benefit of being designed to adapt to the type of device that you are using, so you don't have to think about it.

Download any template to start with.

In the future there are tools like Jekyll, which could make your website life easier. (This website is made using Github and jekyll).

## Step 3: Make local repository
Create a folder on your computer with the same name as the one you created on github. i.e ``jsmith.github.io``. This will be the location of file for the website.

## Step 4: Put template in local repository
Extract the selected template into the repository you created onto your local machine. There should be a file called ``index.html``. This file should be at the base level of the repository.

This `index.html` is the webpage for the homepage of the website. Everything that appears in `index.html` is what will appear when someone goes to ``<USERNAME>.github.io``.

## Step 5: Git add/commit/push to remote
Now to push the website template to github. You will need to add the remote repository as the origin.:

```
git init
git remote add origin https://github.com/<USERNAME>/<USERNAME>.github.io
```
Then commit and push to the origin:

```
git add -A
git commit -m "Initial commit of my website"
git push origin main
```

You should now be able to go to the url ``<USERNAME>.github.io`` and view your website.

<mark>
Note: Sometimes that doesn't work and you see a blank page.
</mark>

<mark>
To fix this go to settings > options. Click "Choose a Theme" in the Github Pages section. Then click "Select Theme" (It doesn't matter what you select). Then it should work when you go to `USERNAME.github.io`. You might have to wait a couple of minutes for the website to update.
</mark>

## Step 6: Modifying the template
Obviously you are going to modify the template. This can be done by editing the ``index.html`` file. 
``index.html`` is the home page of the website. Some themes come with additional pages such as ``generic.html`` or ``elements.html``.

- ``generic.html``: This is a generic additional page for your website, you can duplicate this to make many pages.
- ``elements.html``: This page lists a bunch of different icons, buttions and objects you can add to your website. By looking at the htlm you can work out how to use them.

This tutorial wont cover how to write html and css code. But you should be able to workout which text to replace by looking at the source code and how it is displayed on the website. 
A little trial and error can go a long way.
