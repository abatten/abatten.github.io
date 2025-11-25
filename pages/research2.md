---
layout              : page-fullwidth
show_meta           : false
title               : "Research"
subheadline         : ""
teaser              : ""
header:
   title            : ' '
   image_fullwidth  : "milky-way.jpg"
permalink           : "/research/"
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

I am trained as an astronomer, so my research broadly revolves around trying to understand the Universe.
My work typically involves using large computer simulations or other forms of 'Big Data'.
I am usually a theorist and like working with simulations of all sorts. However, I do occasionally dabble with observations and even human-based experiments.

I am currently a Neuroimaging Informatics Fellow at Swinburne University of Technology, where I develop data analysis pipelines and software infrastructure for processing large neuroimaging datasets using high-performance computing systems. I also develop tutorials for users of OzSTAR to make it easier to analise their data.

My recent research has been highly multi-disciplinary. I have been modelling the magnetic fields of the brain for magnetoencephalography (MEG) imaging as part of the Critical Technologies Challenge Program. I have investigated how primordial black holes could delay recombination and potentially resolve the Hubble tension. I worked with the City of Boroondara to assess satellite imagery for monitoring urban tree canopy coverage. I have used the Hubble Space Telescope to measure the expansion rate of the Universe with Tip of the Red Giant Branch stars. I have also worked on active space domain awareness to track satellites and determine what to do when we lose track of one.

My PhD research revolved around studying the intergalactic medium and how its evolution can inform us about the history of galaxies. I used cosmological hydrodynamic simulations to determine how fast radio bursts can probe the effects of active galactic nuclei and the ionised gas in the intergalactic medium.


My list of publications are avaliable on <a href="https://ui.adsabs.harvard.edu/public-libraries/JVI0wKk5ThW2taKTMT2oEQ">ADS</a>, via my <a href="https://orcid.org/0000-0001-7599-6488">ORCID page</a> and <a href="https://scholar.google.com/citations?user=aRUJW5UAAAAJ&hl=en">google scholar</a>.

My recent scientific and public talks list is on my [talks](/talks) page.

## Research Interests
### Astronomy Interests
[Cosmic Expansion and Hubble Tension](#cosmic-expansion-and-hubble-tension){:.button}
[Primordial Black Holes (PBHs)](#primordial-black-holes){:.button}
[The Intergalactic Medium](#the-intergalactic-medium){:.button}
[Galaxy Evolution](#galaxy-evolution){:.button}
[Fast Radio Bursts (FRBs)](#fast-radio-bursts){:.button}

### Non-Astronomy Research Interests
[Magnetoencephalography (MEG)](#magnetoencephalography){:.button}
[Earth Observation and Tree Canopy Coverage](#tree-canopy-coverage-in-the-city-of-booroondara){:.button}
[Space Domain Awareness](#space-domain-awareness){:.button}
[Artificial Intelligence as a Team Member](#ai-as-a-team-member){:.button}


## Research Projects
### Magnetoencephalography
**I developed software to simulate and visualise the magnetic fields around brains in order to develop revolutionary new devices for a medical imaging technique called 'magnetoencephalography' or MEG. This research is part of the Critical Technologies Challenge Program (CTCP) from the Australian Department of Industry, Science & Resources (DISR).**

!["A visualisation of the cosmic distance ladder to measure H0 from supernovae."](/images/research/MEG/Brain_Model_1.png)
<!--!["A visualisation of the cosmic distance ladder to measure H0 from supernovae."](/images/research/MEG/Brain_Model_2.png)-->

When we perform a task, like lifting an arm, or thinking about a dog, the neurons in our brain generate electric currents in order to send this information where it needs to go. 
These electric currents result in very small (~ 1e-14 Tesla), but measurable magnetic fields around our brain. 
These magnetic fields can be detected using a technique called 'magnetoencephalography (MEG)'. 
This is a non-invasive technique provides extremely high temporal resolution, allowing us to measure and observe changes in brain activity on millisecond timescales. 
The ability to measure neurological activity of millisecond timescales makes MEG an ideal tool for monitoring conditions such as concussion, depression, epilepsy and Alzheimer's disease.

However, current generation of MEG machines require a very expensive shielded rooms to exclude all external magnetic fields in order to measure the very tiny signals caused by brain activity. 
This is both very costly (about a million dollars per room), but also limits, portability and access to these devices. 

I work on modelling and simulating the magnetic fields around the brain to develop new diamond based MEG sensors, with the goal of building a new device that doesn't require a magnetically shielded room. 
These devices would be significantly cheaper and more portable than current technologies, allowing for a larger number of people tov receive the monitoring and treatment they need.  


### Cosmic Expansion and Hubble Tension
**I am using the Hubble Space telescope and the Tip of the Red Giant Branch Stars to measure the expansion rate of the Universe.**

!["A visualisation of the cosmic distance ladder to measure H0 from supernovae."](/images/research/distance_ladder.png)
<sup>Image Credit: NASA, ESA and A. Feild (STScI)</sup>

Our Universe is expanding at an accelerating rate.
The present-day Hubble parameter (H0) quatifies how fast the Universe is expanding and can be measured in various ways.
However, there is a discrepency between measurements of H0 that are made locally (using the cosmic distance ladder), and the value of H0 infered from the cosmic microwave background (CMB).
These values are 73.30 ± 1.04 km s-1 Mpc-1 (local measurements using Cepheid calibrated Supernovae) and 67.8 +/- 0.9 (CMB measured by Planck), a 5 sigma difference.
As H0 is a crucial parameter in the standard model of cosmology, it is necessary to improve the significance of these results.
In my research I am using the Hubble Space telescope and the tip of the red giant branch (TRGB) as an alternative distance indicator to the Cepheid period luminosity (Leavitt) relation.


### Primordial Black Holes
**I have used simulations of the early Universe during recombination to study the effect primordial black holes as potential dark matter candidates and their role in the Hubble tension (Batten & Mould 2025)**

!["NASA's artist concept of primordial black holes"](/images/research/pbhs_nasa.jpg)
<sup>Image Credit: NASA's Goddard Space Flight Center</sup>

Most black holes that we know about today formed when massive stars collapsed at the end of their lives.
However, there is another type of hypothetical black hole that could have formed much earlier in the history of the universe, shortly after the Big Bang. These are called 'primordial black holes (PBHs)' and they would have formed from extremely dense regions of matter that collapsed under their own gravity when the universe was less than a second old.
Unlike stellar black holes, primordial black holes could have a wide range of masses, from as small as an asteroid to many times the mass of our Sun.

One of the most exciting possibilities is that primordial black holes could make up some or all of the mysterious dark matter that comprises about 85% of all matter in the universe.
However, we don't yet know if primordial black holes actually exist, as they are extremely difficult to detect and observe directly.

I am using recombination simulations to study how the evaporation of primordial black holes through Hawking radiation would affect the cosmic microwave background (CMB) and potentially contribute to resolving the Hubble tension.
When PBHs evaporate, they inject energy into the surrounding plasma, which could alter the timing and efficiency of recombination when the first atoms formed.
This work helps determine whether primordial black holes could explain some of the discrepancies we observe in measurements of the universe's expansion rate.

### Tree Canopy Coverage in the City of Booroondara
**I worked with the City of Booroondara to assess the suitability of using satellite imagery to monitor tree canopy coverage and detect illegal tree removals.**

!["A image showing an Earth observation of CoB in RGB and also 7 different vegetation indicies"](/images/research/vegindex.png)

Tree canopy coverage is an important factor in city planning and environmental sustainability, providing benefits like reduced urban heat, improved air quality, and stormwater management.
Currently, to measure tree canopy coverage across a municipality, a plane is flown over the area to capture high resolution aerial photographs. However, this expensive surveying method is typically only conducted once every year or two, which means the information can quickly go out of date as trees are removed, planted, or naturally change over time. The infrequent nature of these surveys also makes it difficult to detect when trees have been illegally removed, as the damage may not be discovered for many weeks or months after the removal.

I worked with the City of Booroondara to assess whether satellite imagery could provide a more cost-effective and timely alternative for monitoring urban tree canopy. 
Satellites can capture images of the same area multiple times per week providing much higher temporal resolution than traditional aerial surveys. Using Earth observation data offers the potential for city councils to have up-to-date information about the locations of tree canopy, and potentially able to identify new locations for trees to be planted. 

Using remote sensing and machine learning techniques to process these satellite images, I detected and classified vegetation coverage, and provided a value judgment for the type of data required for different types of analysis. 

### Space Domain Awareness
**I developed novel analysis and visualisation techniques for actively tracking satellites and predicting their future positions.**

!["A visualisation of a large number of GEO satellites and their error bars"](/images/research/sda_roo.png)

With thousands of satellites orbiting Earth and the number increasing rapidly each year, keeping track of all these objects has become a critical challenge for space agencies and operators around the world.
Space Domain Awareness (SDA) is the practice of monitoring and cataloguing all artificial objects in Earth's orbit, from large operational satellites down to small pieces of space debris.

However, satellites don't always remain visible to ground-based telescopes due to factors like Earth's shadow, atmospheric conditions, or simply because they pass outside the field of view of tracking stations.
When we lose track of a satellite, it becomes difficult to predict where it will be when it next becomes observable, which can lead to potential collisions or interference with other space based objects. Additionally, sometimes an unknown satellite can be detected in orbit, and the goal is to determine *What is this satellites?* and *Is this a threat?* as fast as possible.

I worked on 'Active Space Domain Awareness' (Active-SDA), a collaboration between Swinburne, RMIT and CGI Space, where instead of passively waiting for satellites to reappear, we actively predict where they should be and target our follow-up observations accordingly. This involves using orbital mechanics and algorithms to model satellite trajectories and account for various perturbations that affect their orbits, such as atmospheric drag and solar radiation pressure.

By accurately predicting where a satellite will be at a given time, we can point our telescopes to the right location and quickly re-establish tracking, reducing the risk of losing valuable space assets and improving overall space situational awareness.


### AI as a Team Member
Human performance in time-critical decision making is influenced by a combination of mental workload, stress, situational awareness and expertise.
Decision-making processes in high-risk, time-pressured scenarios are now regularly supported by artificial intelligence (AI), however,
the integration of computational support through the inclusion of one or more AI team members needs to be approached thoughtfully.
In this project I am investigating the role of an AI team-member as a monitors for individuals performance, and the characteristics and effectiveness of human-AI teams.

### Fast Radio Bursts
**I developed a software tool called *FRUITBAT*, to estimate the distances to fast radio bursts, based on their observed dispersion measure (Batten 2019).**
!["An artists interpretation of an FRB being detected at the Molonglo Radio Telescope."](/images/frbs.jpg)
<sup>Image Credit: James Josephides / Swinburne University of Technology.</sup>

Fast radio bursts (FRBs) are a class of bright, millisecond, extragalactic radio transients.
In the short time since their discovery in 2007, they are already a valuable tool for studying the Universe.
The critical property of FRBs is their dispersion measure (DM), which is a measure of how delayed different frequencies are due to the material along the sightline to the burst.
An FRBs dispersion measure is extremely sensitive to the total number of electrons along their line-of-sight.
Due to the extragalactic nature of FRBs (they come from galaxies outside of our own), their dispersion measure makes them an excellent probe of the highly ionised plasma that fills the intergalactic medium.

### The Intergalactic Medium
**I measured the electron density in large simulations of the Universe to predict where *fast radio bursts* intersect cosmic filaments of the intergalactic medium (Batten et al. 2021).**

!["A visualisation of the filaments of the intergalactic medium and cosmic web from the EAGLE simulations."](/images/eagle_igm.jpg)
<sup>Image Credit: The EAGLE Project</sup>

The majority of the matter in the Universe can not be found inside galaxies. Instead, most of the mass of the Universe (about 80% of present-day baryons) resides in the low-density, highly ionised region outside of galaxies known as the *Intergalactic Medium* (IGM).
The fact that the IGM contains the vast majority of the mass of the Universe means it is a crucial component to study if we wish to have a complete understanding of the evolution of matter.

Additionally, the IGM is tightly linked to the evolution of stars and galaxies.
The IGM provides the initial conditions from which a galaxy grows, and is the reservoir of pristine gas which galaxies accrete to form new stars.
There is also a significant amout of outflows from galaxies that heats the IGM and enriches it with metals.
The intertwined nature of galaxy evolution and the IGM means it is impossible to disentangle them and study them individually. To understand one, we must understand the other.
However, the IGM isn't so easy to observe.
The high-temperatures and low-densities make observations in the optical and UV extremely unfavourable.

In my PhD, I looked at using fast radio bursts to probe the intergalactic medium and galaxy evolution. In particular, I determined that it is possible to use fast radio bursts to constrain feedback from active galactic nuclei.

### Galaxy Evolution
**I showed that with enough fast radio bursts we can constrain feedback from active galactic nuclei (Batten et al. 2022)**

Galaxy evolution is the study of how galaxies form, grow, and change over cosmic time. Galaxies don't exist in isolation—they continuously interact with their surroundings, accreting gas from the intergalactic medium to form new stars and expelling material back out through powerful outflows. One of the most important processes affecting galaxy evolution is feedback from active galactic nuclei (AGN), which are supermassive black holes at the centres of galaxies that can release enormous amounts of energy. This AGN feedback heats and pushes gas out of galaxies, regulating star formation and shaping the properties of galaxies we observe today.

However, measuring the impact of AGN feedback is extremely challenging because it occurs over vast cosmic scales and timescales. In my research, I used fast radio bursts as a novel probe to detect the effects of AGN feedback on the intergalactic medium. When AGN inject energy into their surroundings, they heat and ionise the gas, changing its electron density distribution. Fast radio bursts are sensitive to these changes through their dispersion measure. By analysing dispersion measures from simulations with different AGN feedback models, I demonstrated that we can use fast radio bursts to constrain how much energy AGN inject into the intergalactic medium, providing a new tool for understanding galaxy evolution.


---
## Publications
My list of my publications are also avaliable on <a href="https://ui.adsabs.harvard.edu/public-libraries/JVI0wKk5ThW2taKTMT2oEQ">ADS</a>, via my <a href="https://orcid.org/0000-0001-7599-6488">ORCID page</a> and <a href="https://scholar.google.com/citations?user=aRUJW5UAAAAJ&hl=en">google scholar</a>.

#### First Author Papers
**Batten, A. J.** & Mould, J., "The impact of Hawking radiation from primordial black holes on recombination and the Hubble tension" (sumitted to MNRAS)

**Batten, A. J.**, et al., "Fast radio bursts as probes of feedback from active galactic nuclei", *Monthly Notices of the Royal Astronomical Society: Letters*, vol. 512, iss. 1, May 2022, Pages L49-L53, <a href="https://doi.org/10.1093/mnrasl/slac020">https://doi.org/10.1093/mnrasl/slac020</a>

**Batten, A. J.**, et al., "The cosmic dispersion measure in the EAGLE simulations", *Monthly Notices of the Royal Astronomical Society*, vol. 505, iss. 4, August 2021, Pages 5356–5369, <a href="https://doi.org/10.1093/mnras/stab1528">https://doi.org/10.1093/mnras/stab1528</a>

**Batten, A. J.**, "Fruitbat: A Python Package for Estimating Redshifts of Fast Radio Bursts", *The Journal of Open Source Software*, vol. 4, no. 37, 2019.
<a href="https://doi.org/10.21105/joss.01399">https://doi.org/10.21105/joss.01399</a>.

---
## Software
#### FRUITBAT
 FRUITBAT is an open source fast radio burst (FRB) redshift estimation package written in Python.
 <a href="https://github.com/abatten/fruitbat"> Repo on Github</a>

