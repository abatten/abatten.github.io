---
#
# Use the widgets beneath and the content will be
# inserted automagically in the webpage. To make
# this work, you have to use › layout: frontpage
#
layout: frontpage
header:
  image_fullwidth: cosmic-web.jpg

widget1:
  title: "Blog & Portfolio"
  url: 'http://phlow.github.io/feeling-responsive/blog/'
  image: widget-1-302x182.jpg
  text: 'Every good portfolio website has a blog with fresh news, thoughts and develop&shy;ments of your activities. <em>Feeling Responsive</em> offers you a fully functional blog with an archive page to give readers a quick overview of all your posts.'

widget2:
  title: "Why use this theme?"
  url: 'http://phlow.github.io/feeling-responsive/info/'
  text: '<em>Feeling Responsive</em> is heavily customizable.<br/>1. Language-Support :)<br/>2. Optimized for speed and it&#39;s responsive.<br/>3. Built on <a href="http://foundation.zurb.com/">Foundation Framework</a>.<br/>4. Seven different Headers.<br/>5. Customizable navigation, footer,...'
  video: '<a href="#" data-reveal-id="videoModal"><img src="http://phlow.github.io/feeling-responsive/images/start-video-feeling-responsive-302x182.jpg" width="302" height="182" alt=""/></a>'

widget3:
  title: "Download Theme"
  url: 'https://github.com/Phlow/feeling-responsive'
  image: widget-github-303x182.jpg
  text: '<em>Feeling Responsive</em> is free and licensed under a MIT License. Make it your own and start building. The code is well-documented and explains you how it works.'
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
callforaction:
  url: https://tinyletter.com/feeling-responsive
  text: Inform me about new updates and features ›
  style: alert
permalink: /index.html
#
# This is a nasty hack to make the navigation highlight
# this page as active in the topbar navigation
#
homepage: true
---


<div style="width:30%; margin:0 auto;" align="center" markdown="1">
![Avatar](/assets/images/avatar.jpg){:.small.circle.border.shadow}
</div> 

<h1 style="text-align: center;">
Adam Batten
</h1>

<h3 style="text-align: center;">
Hi! I'm Adam, an astronomer from Australia. 
</h3>

<h5 style="text-align: center;">
I study the intergalactic medium, the hot, tenuous material that fills the space between galaxies. 

</h5>
I am currently a PhD candidate in the [Centre for Astrophysics and Supercomputing](https://astronomy.swin.edu.au/) at the Swinburne University of Technology.
My primary interest is using large simulations to study the composition and evolution of the intergalactic medium through cosmic time. 
My research is part of the ARC Centre of Excellence for All-Sky Astrophysics in 3 Dimensions ([ASTRO 3D](https://astro3d.org.au/)). 

You can see more about my research on my [research page](research.html) and my list of publications on <a href="https://ui.adsabs.harvard.edu/search/q=docs(library%2FJVI0wKk5ThW2taKTMT2oEQ)&sort=date%20desc%2C%20bibcode%20desc&p_=0">ADS</a>.

### Contact Details
Email: abatten*[at]*swin.edu.au

Mail Address: Mail Number H29, PO Box 218, Hawthorn, VIC 3122, Australia 



<div id="videoModal" class="reveal-modal large" data-reveal="">
  <div class="flex-video widescreen vimeo" style="display: block;">
    <iframe width="1280" height="720" src="https://www.youtube.com/embed/3b5zCFSmVvU" frameborder="0" allowfullscreen></iframe>
  </div>
  <a class="close-reveal-modal">&#215;</a>
</div>
