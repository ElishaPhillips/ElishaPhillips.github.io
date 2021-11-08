---
title: Quantum Dots 
subtitle: Analyzing Charge Stability.
date: 2019-07-24 00:00:00
description: 
featured_image: "/project_data/quantum-dot-charge-stability/D2_3D_Still.PNG"
accent_color: '#4C60E6'
gallery_images:
  - demo.jpg
  - demo.jpg
  - demo.jpg
---

{% if page.htmlwidgets %}
{% for html_dep in site.static_files %}
  {% if html_dep.path contains 'htmlwidgets_deps/' %}
    {% assign start = "<script src=" | append: {{site.baseurl}} %}
    {{html_dep.path | prepend: start | append: "></script>" }}
    {% endif %}
  {% endfor %}
{% endif %}


#### Reference:
[Qubits made by advanced semiconductor manufacturing](https://arxiv.org/abs/2101.12650#)

*Data from: https://doi.org/10.5281/zenodo.4478855*

#### Pt. I 

Initial Data Plots, from Fig. 2:

*Using the included Figure_2.py as reference for important parameters, such as removing data offsets and converting current to pA, saved in 3400 dpi*

The lines represent Coloumb barriers - sweeping along G3 manipulates electrochemical pot. of Si quantum dot with G2 and G4 manipulating the tunneling barriers:

![D5+6](https://github.com/ElishaPhillips/Quantum_Dot_Charge_Stability/blob/6679d233628fa045aa92d779668f77d3ae79c5d0/Graphs/D56.png)
*Each line represents the transmission of a single electron*

Double Dot Stability:

*As C<sub><sub>m</sub></sub> shifts from 0 to C<sub><sub>m</sub></sub>/C<sub><sub>1,2</sub></sub> = 1 through adjusting G4 voltage:*

![D1](https://github.com/ElishaPhillips/Quantum_Dot_Charge_Stability/blob/6679d233628fa045aa92d779668f77d3ae79c5d0/Graphs/D1.png)
![D2](https://github.com/ElishaPhillips/Quantum_Dot_Charge_Stability/blob/6679d233628fa045aa92d779668f77d3ae79c5d0/Graphs/D2.png)
![D3](https://github.com/ElishaPhillips/Quantum_Dot_Charge_Stability/blob/6679d233628fa045aa92d779668f77d3ae79c5d0/Graphs/D3.png)
![D4](https://github.com/ElishaPhillips/Quantum_Dot_Charge_Stability/blob/6679d233628fa045aa92d779668f77d3ae79c5d0/Graphs/D4.png)


<head>
  <style> iframe { border: none } </style>
</head>
<body>
  <iframe src="https://github.com/ElishaPhillips/Quantum_Dot_Charge_Stability/blob/ce1bbe2a90d77dfc2425dc79fbfec5e6a0ff13fd/D2-3d.a.html"
          width="100%" height="100%" allowfullscreen sandbox>
  </iframe>
</body>


**Obviously,** we’ve styled up *all the basic* text formatting options [available in markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).

You can create lists:

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

{% include /project_data/quantum-dot-charge-stability/D2-3d.a.html}

### Pretty cool, huh?

We've packed this theme with powerful features to show off your work.
Why not put them to use on your new website?

<a href="https://jekyllthemes.io/theme/made-portfolio-jekyll-theme" class="button--fill">Get This Theme</a>
