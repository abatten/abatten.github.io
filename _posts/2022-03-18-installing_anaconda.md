---
layout: page-fullwidth
title: "Installing Python with Anaconda"
subheadline: ""
meta_teaser: "A guide for installing Python for the first time."
teaser: "A guide for installing Python for the first time."
header:
    image: homepage_typography.jpg
    background-color: "#262930"
    caption: This is a caption for the header image with link
    caption_url: https://unsplash.com/
image:
    thumb:  homepage_typography-thumb.jpg
    homepage: homepage_typography.jpg
    caption: Image by Antonio
    caption_url: "http://www.aisleone.net/"
categories:
    - tutorial

permalink           : "/tutorials/installing_anaconda/"
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


# A Guide to Installing Python with Anaconda.

This tutorial is a write up of the installation instructions used for my "Introduction to Python Workshops" that I ran at Swinburne University of Technology. 
These workshops were targeted at Year 10 work experience students to learn the basics of loading data nd plotting with Python.
{:.success}

## Python 
Python is a programming language that is very popular and is used by many astronomers to perform their research. Some of the uses of Python include reading telescope data, analysing simulations and making graphs/plots of results. If you were you were to google 'Install Python' you would see many different options and versions of Python to install and from dfferent locations. It isn't particularly clear which one you should use, how to install it and how to use it one you have.

Additionally, if you are using MacOS or Linux your computer likely already has a version of Python already installed to run the operating system. So installing a new version may cause some conficting issues with your computer, particularly if when you want to install more 'Python packages' (we will get to this later).

However there is much easier and better way to install Python. This is through using Anaconda.


## Downloading and Installing Anaconda
Anaconda is distribution of Python designed for scientific computing. By installing Python through Anaconda, it makes managing and installing Python packages/versions significantly easier

You should be able to follow these instructions to install Anaconda on your system:

- Go to [https://www.anaconda.com/products/individual](https://www.anaconda.com/products/individual) and click on 'Download'. It should take you to the bottom of the page to the different options (see Figure 1 below).
- Choose the installer for your operating system. You will probably want to use the graphical installer since it is much easier. **Windows users note:** You can only use a graphical installer, but you need to check if your system is 64-bit (most likely) vs 32-bit, then choose the appropriate one. You can check which type your computer is by <a href="https://support.microsoft.com/en-us/windows/32-bit-and-64-bit-windows-frequently-asked-questions-c6ca9541-8dce-4d48-0415-94a3faa2e13d">clicking here</a> and following the instructions. 
- After the download completes, double click on the file to open the installer. It should like Figure 2 on Windows 10 or Figure 7 on MacOS Big Sur.
- Then follow either the [Windows 10](#windows-10-installation) or [MacOS](#macos-installation) installation instructions that follows.

<p><img src = "/assets/images/tutorials/anaconda_install/anaconda_install_0.png"></p> 
<p><small align="center">Figure 1 - Anaconda installation options. Choose the one that is appropriate for your computer.</small></p>

### Windows 10 Installation
- Click 'I Agree' to the licensing agreement (see Figure 3). 
- Select to install for 'Just Me' then click 'Next'.
- Choose location to install. The default location should be something `C:\\Users\<NAME>\anaconda3`. This default location is normally recommended, but you can install it elsewhere.
- Tick the boxes that say *'Add Anaconda3 to my PATH environment variable'* and *'Register Anaconda3 as my default Python 3.8'*. See Figure 4. It will likely have a red warning that says the first option is not recommended, because it 'makes anaconda get found before previously installed software', but that is actually what we want to happen. It might also say a different number to Python 3.8 (i.e Python 3.9, 3.10, etc..), this is also okay.
- Continue to Section [Anaconda Navigator](#anaconda-navigator).

<p><img src = "/assets/images/tutorials/anaconda_install/anaconda_install_1.png"></p>
<p align = "center"><small>Figure 2 - Anaconda Installer (Windows 10)</small></p>

<p><img src = "/assets/images/tutorials/anaconda_install/anaconda_install_2_windows.png"></p>
<p align = "center"><small>Figure 3 - Anaconda License Agreement (Windows 10)</small></p>

<p><img src = "/assets/images/tutorials/anaconda_install/anaconda_install_6_windows.png"></p> 
<p align = "center"><small>Figure 4 - Anaconda installation options on Windows 10. You want to tick both boxes.</small></p>


### MacOS Installation
- Click 'Continue' on Read Me to get to the licensing agreement. 
- Click 'Continue' then 'I Agree' to the licensing agreement (see Figure 7). 
- Click 'Install' on installation type. This will install anaconda in the default location, this is usually `/Users/<NAME>/opt/anaconda3`.
- Click 'Continue' after the installation is complete.
- Continue to Section [Anaconda Navigator](#anaconda-navigator).


<p><img src = "/assets/images/tutorials/anaconda_install/anaconda_install_1_mac.png"></p> 
<p align = "center"><small>Figure 6 - Anaconda Installer (MacOS)</small></p>


<p><img src = "/assets/images/tutorials/anaconda_install/anaconda_install_2_mac.png"></p> 
<p align = "center"><small>Figure 7 - Anaconda License Agreement (MacOS)</small></p>



## Anaconda Navigator
To check that Anaconda has been correctly installed we will attempt to open the Anaconda Navigator. You can load this program by doing the folowwing: 

- **Windows:** Click the home button and search for 'anaconda navigator', then click to open
- **MacOS:** Click 'Launchpad' and search 'anaconda-Navigator', then click to open.

The program should look something similar to Figures 8 (Windows) and 9 (MacOS). Note that you may have different icons or tiles showing based on what is already installed on your computer. The important thing you should be able to see is something called 'JupyterLab' and 'Jupyter Notebook'. If you can see both of these, then it has installed correctly and you are ready to start using Anaconda and Python.

<p><img src = "/assets/images/tutorials/anaconda_install/anaconda_navigator_windows.png"></p> 
<p align = "center"><small>Figure 8 - Anaconda Navigator in Windows 10</small></p>

<p><img src = "/assets/images/tutorials/anaconda_install/anaconda_navigator_macos.png"></p> 
<p align = "center"><small>Figure 9 - Anaconda Navigator in MacOS</small></p>
