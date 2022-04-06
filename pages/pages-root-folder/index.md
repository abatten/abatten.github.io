---
#
# Use the widgets beneath and the content will be
# inserted automagically in the webpage. To make
# this work, you have to use › layout: frontpage
#
layout: frontpage
header:
  title: ' ' 
  image_fullwidth: milky-way.jpg

widget1:
  title: "Recent Publication"
  url: 'https://arxiv.org/abs/2109.13472'
  image: CDF_distance.png
  text: 'Check out my latest research paper titled: <i>Fast radio bursts as probes of feedback from active galactic nuclei</i>'

widget2:
  title: "Fruitbat"
  url: 'https://github.com/abatten/fruitbat'
  image: fruitbat_badge1.png
  text: I am the lead developer on <i>Fruitbat</i>. A Python package for estimating redshifts for Fast Radio bursts.

widget3:
  title: "Science Talks: Recordings & Slides"
  url: '/talks/'
  image: adam_asa_2021.jpeg
  text: 'See recordings and slides from my previous conference and invited talks'

#
# Use the call for action to show a button on the frontpage
#
# To make internal links, just use a permalink like this
# url: /getting-started/
#
# To style the button in different colors, use no value
# to use the main color or success, alert or secondary.
# To change colors see sass/_01_settings_colors.scss
#
#callforaction:
#  url: https://tinyletter.com/feeling-responsive
#  text: Inform me about new updates and features ›
#  style: alert
permalink: /index.html
#
# This is a nasty hack to make the navigation highlight
# this page as active in the topbar navigation
#
homepage: true
---

# Dr. Adam Batten
{: style="text-align: center;"}

## Hi! I'm Adam, an astronomer from Australia. 
{: style="text-align: center;"}

### I study the intergalactic medium, the hot, tenuous material that fills the space between galaxies. 
{: style="text-align: center;"}


<div style="text-align: center;">
<img class="t60" src="{{ site.urlimg }}avatar.jpg" alt="A portrait photo of Adam Batten" height="30%" width="30%" style="border-radius: 50%">
</div>

<div id="videoModal" class="reveal-modal large" data-reveal="">
  <div class="flex-video widescreen vimeo" style="display: block;">
    <iframe width="1280" height="720" src="https://www.youtube.com/embed/3b5zCFSmVvU" frameborder="0" allowfullscreen></iframe>
  </div>
  <a class="close-reveal-modal">&#215;</a>
</div>
