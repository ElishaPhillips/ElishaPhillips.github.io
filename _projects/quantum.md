---
title: 'Quantum Dots'
subtitle: 'Data Analysis and Visualization'
date: 2021-11-14 00:00:00
description: Extracting critical features from published charge stability datasets measured from two Si Quantum Dots.
featured_image: AdobeStock_320419547.png
gallery_images:
  - AdobeStock_320419547.png
---


# Abstract
> "Semiconductor-based quantum computing is promising as it provides potential for the integration of qubits with their control and readout circuits on a single chip. This paves the way for the realization of a large-scale quantum computing system."

#### The practicality of these systems relies on an effective method of reading and manipulating these qubits, and the charge stability diagram provides an essential role in this process. Here, I explore and analyze such a dataset from the paper *‘Qubits made by advanced semiconductor manufacturing’* (2021) which seeks to establish the feasibility of present silicon manufacturing methods towards the future of practical quantum computing.  


#### With this project I worked to build a better understanding of the quantum double dot systems and demonstrate novel approaches for the visualization and modeling the potential landscape of a double quantum dot system measured in a 2 -Dimensional electron gas in a Si substrate. 

# Overview


<iframe title="D2" aria-label="Interactive line chart" id="D23D" src="/images/projects/Quantum/Figures/D2-3d.a.html" scrolling="no" frameborder="0" style="width: 100%; min-width: 200% !important; border: none;"></iframe>


An excellent resource throughout this process, in addition to the above referenced paper, was ‘Electron transport through double quantum dots’ (2003) , detailing the mechanics of the double quantum dot system, and the relevancy of the charge stability diagram in their application. Briefly, the quantum dots are measured with two swept gate voltages that manipulate the electrochemical potential between the two, a process suppressed by the Columb Blockade effect for sufficiently low voltages. As the gate voltages are swept, conductive coupling between the dots increases until the charge states become degenerate, a delocalized amplitude between the two dots.

The hole transfer process:

Where the dots cycle through the sequence  (N1 , N2)→(N1,1 N2)→(N1 , N2,1)→(N1 ,N2)
Which sequentially tunnels an electron from the left to the right lead, 
And the opposing case, the hole transfer process:  
N1+11,N211!→~N111,N2!→~N1 ,N211! →~N111,N211!

It should be noted that this delocalization causes the interdot eigenenergies to be linearly dependent on the input gate parameters and the Coloumb repulsion at these triple dot points, thus allowing us to characterize the energetics of the system without computing the eigenergy value of the dots. (Quantum Theory, 2011)

Process:
I used QTT to import the downloaded dataset and assigned the four charge stability diagrams to their respective databases. Using the attatched .py file to locate the input parameters for offset and conversion from the imported databases I recreated the original figures referenced and stored them in higher resolution images to get an initial overview:

I then used plotly to recreate Figure 2d in an interactive 3d surface graph: 

# Discussion

![](/images/projects/Quantum/AdobeStock_332906314.png)

# Methods 

![](/images/projects/Quantum/AdobeStock_332906314.png)

# Results 

![](/images/projects/Quantum/AdobeStock_378614280.png)

# Discussion

![](/images/projects/Quantum/AdobeStock_467591331.png)

Bulleted list

* Simple bulleted lists
* Like this one
* Are cool

And:

1. Numbered lists
2. Like this other one
3. Are great too

You can also add blockquotes, which are shown at a larger width to help break up the layout and draw attention to key parts of your content:

> “Simple can be harder than complex: You have to work hard to get your thinking clean to make it simple. But it’s worth it in the end because once you get there, you can move mountains.”

The theme also supports markdown tables:


| Item                 | Author        | Supports tables? | Price |
|----------------------|---------------|------------------|-------|
| Duet Jekyll Theme    | Jekyll Themes | Yes              | $49   |
| Index Jekyll Theme   | Jekyll Themes | Yes              | $49   |
| Journal Jekyll Theme | Jekyll Themes | Yes              | $49   |

And footnotes[^1], which link to explanations[^2] at the bottom of the page[^3].

[^1]: Beautiful modern, minimal theme design.
[^2]: Powerful features to show off your work.
[^3]: Maintained and supported by the theme developer.

You can throw in some horizontal rules too:

---

#### Image galleries

Here's a really neat custom feature we added – galleries:

{% include post-components/gallery.html
	columns = 2
	full_width = true
	images = "/images/demo.jpg,/images/demo.jpg,/images/demo.jpg,/images/demo.jpg,
	"
%}

Inspired by the Galleries feature from WordPress, we've made it easy to create grid layouts for your images. Just use a simple Liquid snippet in your post to create a masonry grid image layout:

{% raw %}
```liquid
{% include post-components/gallery.html
	columns = 2
	full_width = true
	images = "/images/demo.jpg,/images/demo.jpg,/images/demo.jpg,/images/demo.jpg,
	"
%}
```
{% endraw %}

*See what we did there? Code and syntax highlighting is built-in too!*

Change the number inside the 'columns' setting to create different types of gallery for all kinds of purposes. You can even click on each image to seamlessly enlarge it on the page.


#### Image carousels

Here's another gallery with only one column, which creates a carousel slide-show instead.

A nice little feature: the carousel only advances when it is in view, so your visitors won't scroll down to find it half way through your images.

{% include post-components/gallery.html
	columns = 1
	full_width = true
	images = "/images/demo.jpg,/images/demo.jpg,/images/demo.jpg
	"
%}

#### What about videos?

Videos are an awesome way to show off your work in a more engaging and personal way, and we’ve made sure they work great on our themes. Just paste an embed code from YouTube or Vimeo, and the theme makes sure it displays perfectly:

{% include post-components/video.html
	url = "https://player.vimeo.com/video/270725085?color=6c6e95&title=0&byline=0"
	full_width = true
%}

### Pretty cool, huh?

We've packed this theme with powerful features to show off your work.
Why not put them to use on your new website?

<a href="https://jekyllthemes.io/theme/made-portfolio-jekyll-theme" class="button--fill">Get This Theme</a>
