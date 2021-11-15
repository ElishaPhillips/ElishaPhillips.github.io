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

With this project, I worked to develop a greater understanding of Quantum Computing double-dot systems. I also demonstrate novel approaches for the visualization and modeling of the potential landscape of a double quantum dot system measured in a 2 -Dimensional electron gas in a Si substrate. This work is a vital exercise; developing interactive visualizations can be leveraged to construct better methodologies and play a critical role in improving a communication framework towards relaying significant findings of complex systems to a general public audience who may not carry such an intensive background.  


# Overview  

>"Large-scale Quantum Computing systems in real-world implementation faces many present obstacles toward such an end. One of the challenges gating the practicality of these systems relies on delivering an effective and scalable method of reading and manipulating these qubits."  

Nonetheless, the prospect is exciting! Additionally, this wouldn't be quite as fun if it were that easy.   

Here, I explore and analyze a recent dataset from the paper _'Qubits made by advanced semiconductor manufacturing'_ (2021[^1]) which seeks to establish the feasibility of present silicon manufacturing methods towards the future of practical quantum computing. Regarding reading and manipulating the qubits from a QC chip, the charge stability diagram is essential in this process. This paper is a collaborative effort between Intel Quantum Labs and Delft Qutech, and the datasets are available for download and exploration.  

An excellent resource throughout this process, in addition to the above-referenced paper, was 'Electron transport through double quantum dots' (2003[^2]), detailing the mechanics of these systems and the relevancy of the charge stability diagram in their application. Briefly, one measures the quantum dots as two gate voltages manipulate the electrochemical potential, a process suppressed by the Columb Blockade effect for sufficiently low voltages. As the gate voltages increase, conductive coupling between the dots increases until the charge states degenerate, a delocalized amplitude between the two dots.  

Notably, this delocalization causes the interdot eigenenergies to be linearly dependent on the input gate parameters and the Coulomb repulsion at these triple-dot points, thus allowing us to characterize the energetics of the system without needing to compute the eigenergy value of the dots. (Quantum Theory, 2011[^3])  

# Tools:  

I performed this analysis in Python, using Jupyter Notebook.  

I used the packages Pandas and Numpy for data frame and array processing, wrangling, and filtering.  

I used Numpy's Eigenvector algorithm and the Quantum Technology Toolbox (QTT) framework from QuTech to initially import the dataset and their model fitting algorithms for plotting Anticrossing.   

For visualizations, I utilized Matplotlib and Plotly, using Plotly to generate the interactive Html graphs embedded here.   

I posted this writeup on a webpage built with Jekyll/Gem and hosted on Github, with various customized CSS/Html/JS elements from a pre-formed template.   

_Note: Due to the nature and limited reliability of properly scaling HTML graphs in an iframe container, mobile viewing has some scaling issues, and Desktop viewing is recommended. In the future, I plan to rebuild the graphs in a Dash framework to fix this issue._  

# Process:  

<iframe title="D2" aria-label="Interactive line chart" id="D23D" src="/images/projects/Quantum/figures/D2-3d.a.html" scrolling="no" frameborder="0" style="width: 0; min-width: 200% !important; border: none;" height=1024></iframe>  

<script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(e){if(void 0!==e.data["datawrapper-height"]){var t=document.querySelectorAll("iframe");for(var a in e.data["datawrapper-height"])for(var r=0;r<t.length;r++){if(t[r].contentWindow===e.source)t[r].style.height=e.data["datawrapper-height"][a]+"px"}}}))}();</script>  
	
I used QTT DelTech's Quantum Technology Toolkit to import the downloaded dataset and assigned the four charge stability diagrams to their respective databases. Using the included .py file to locate the input parameters for offset and conversion from the imported databases, I recreated the original figures referenced to examine in higher resolution and to get an initial overview.  
 
In the below figures, one can see how as a constant voltage G4 increases, the geometric patterns form due to the interdot symmetry, and the three lines of the phase boundary indicate an excellent formation of these delocalized states in the second image. As this voltage increases, these boundaries become parallel as the current can flow freely, and these dots effectively form a single quantum dot. I selected the second dataset for further analysis and produced the 3d surface plot above this section to look at this hexagonal formation in more detail.  

{% include post-components/gallery.html
	columns = 2
	full_width = true
	images = 
"/images/projects/Quantum/figures/D1.png,
/images/projects/Quantum/figures/D2.png,
/images/projects/Quantum/figures/D3.png,
/images/projects/Quantum/figures/D4.png,
/images/projects/Quantum/figures/D56.png
"
%}

The QTT package documentation contains an anticrossing fitting algorithm to estimate the scan lines, basing this computation on a visual detection method of selecting regions based on their pixel color formed by measured current peaks. I used this algorithm to estimate an anticrossing boundary, storing the results in an array to overlay on the following diagram.  

This method is only an initial estimate; however, and fine-tuning these systems requires further investigation. Namely, the peak charge values are not an ideal readout location indicator due to crosstalk, anharmonic resonance, physical imperfections, and other such occurrences. Hence, they aren't a good metric for identifying the discrete energy levels based on the values alone - also, these states don't necessarily form according to the peak values of the system, as demonstrated later. Instead, we can leverage the aforementioned orthogonal nature of this system towards this goal. Here, I chose to use NumPy's standard eigenvector algorithm to isolate the eigenvectors and energies of the charge values.  

This method did prove to be effective. Using Plotly, I created both a vector quiver plot and a streamline plot from the eigenvector dataset to overlay onto this figure. I built the base layer similar to the charge stability diagrams I recreated earlier, using the initial D2 dataset, but instead used a 2D contour to help clarify the features of the graph and overlaid the traces. The streamlines show defined topological features, spiraling inwards towards potential critical points in the landscape. While the accuracy of the inline algorithms estimation is yet to be determined, the relationship with the geometry of the underlying diagram shows a good correlation.  

<iframe title="D2" aria-label="Interactive line chart" id="D23D" src="/images/projects/Quantum/figures/figev.html" scrolling="no" frameborder="0" style="width: 0; min-width: 200% !important; border: none;" height=1024></iframe>  

<script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(e){if(void 0!==e.data["datawrapper-height"]){var t=document.querySelectorAll("iframe");for(var a in e.data["datawrapper-height"])for(var r=0;r<t.length;r++){if(t[r].contentWindow===e.source)t[r].style.height=e.data["datawrapper-height"][a]+"px"}}}))}();</script>  	
	
I attempted to further characterize and filter these features in more depth with a simple filtering algorithm, but I ran into issues establishing a working solution, and further work would be needed. As the dataset is quite large, a possible better approach would be to sample the dataset at various points to fine-tune the filtering algorithm before processing through the original set.  

Instead, I targeted the zero points of the eigenvector's complex elements to filter out and then separated the real counterparts. I also took the corresponding eigenvalues to examine separately. The system still features a fair amount of noise/additional effects, but the patterns are still identifiable. The color scale on these figures was mapped to the measured current in pA, with bright pink representing the peak values and blue representing the lower. I plotted both according to the two gate voltages on the x and y-axis, with z representing the respective eigenenergies and eigenvalues. For a direct comparison, I processed the D4 dataset similarly and plotted the eigenvectors with the resulting graph below. You can see the homogeneity of the current peaks at the higher bias voltages, showing a relative uniformity of the system.   

<iframe title="D2" aria-label="Interactive line chart" id="D23D" src="/images/projects/Quantum/figures/evec_d4.html" scrolling="no" frameborder="0" style="width: 0; min-width: 200% !important; border: none;" height=1024></iframe>  

<script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(e){if(void 0!==e.data["datawrapper-height"]){var t=document.querySelectorAll("iframe");for(var a in e.data["datawrapper-height"])for(var r=0;r<t.length;r++){if(t[r].contentWindow===e.source)t[r].style.height=e.data["datawrapper-height"][a]+"px"}}}))}();</script>  	
		
Below is the D2 dataset, in which I sliced the data along the x-axis to demonstrate an interactive exploration of the structure at different voltage values. In contrast with the above figure, the effects of both the Coulomb barriers and the quantum resonance are present, and the trace slicing here proves to be quite effective in investigating the structure.  

<iframe title="D2" aria-label="Interactive line chart" id="D23D" src="/images/projects/Quantum/figures/evec_d2.html" scrolling="no" frameborder="0" style="width: 0; min-width: 200% !important; border: none;" height=1024></iframe>  

<script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(e){if(void 0!==e.data["datawrapper-height"]){var t=document.querySelectorAll("iframe");for(var a in e.data["datawrapper-height"])for(var r=0;r<t.length;r++){if(t[r].contentWindow===e.source)t[r].style.height=e.data["datawrapper-height"][a]+"px"}}}))}();</script>  

The eigenvalues also tell a story; in the below graph, the 1-Dimensional values are scaled across the Y plane and highlight the correlating energy levels of the system. Along with the origin, one can see the five distinct eigenstates and the formation in the landscape of two discrete levels, i.e., the ground state and the excited state of the two dots!  
	
<iframe title="D2" aria-label="Interactive line chart" id="D23D" src="/images/projects/Quantum/figures/eval_d2" scrolling="no" frameborder="0" style="width: 0; min-width: 200% !important; border: none;" height=1024></iframe>  
	
<script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(e){if(void 0!==e.data["datawrapper-height"]){var t=document.querySelectorAll("iframe");for(var a in e.data["datawrapper-height"])for(var r=0;r<t.length;r++){if(t[r].contentWindow===e.source)t[r].style.height=e.data["datawrapper-height"][a]+"px"}}}))}();</script>  
	
I then separated these two levels via vertically scaling in opposing directions, I chose to use a value of 500 per, but the number here is arbitrary and solely for visual distinction. I additionally filtered out all values below 45 pA to better isolate the current peaks. Much better!   

<iframe title="D2" aria-label="Interactive line chart" id="D23D" src="/images/projects/Quantum/figures/eval_d2_filtered.html" scrolling="no" frameborder="0" style="width: 0; min-width: 200% !important; border: none;" height=1024></iframe>  

<script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(e){if(void 0!==e.data["datawrapper-height"]){var t=document.querySelectorAll("iframe");for(var a in e.data["datawrapper-height"])for(var r=0;r<t.length;r++){if(t[r].contentWindow===e.source)t[r].style.height=e.data["datawrapper-height"][a]+"px"}}}))}();</script>  
	
As the final step in this process, I wrote a simple nearest neighbor algorithm that found the peak values within a small 'box' swept across the x and y-axis. I'd add that there is room for improvement with the efficacy of this algorithm, but this proved to be effective and avoided the inconsistencies of simply isolating the peak current values across the system. I also took the eigenvector graph and mapped a 2mV slice from the origin across the x-axis, retaining the initial parameters for the y axis.  

# Results  

Here is the resulting eigenvector graph, sliced from 3770 mV to 3772 mV:  
	
<iframe title="D2" aria-label="Interactive line chart" id="D23D" src="/images/projects/Quantum/figures/evec_d2_sliced.html" scrolling="no" frameborder="0" style="width: 0; min-width: 200% !important; border: none;" height=1024></iframe>  

<script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(e){if(void 0!==e.data["datawrapper-height"]){var t=document.querySelectorAll("iframe");for(var a in e.data["datawrapper-height"])for(var r=0;r<t.length;r++){if(t[r].contentWindow===e.source)t[r].style.height=e.data["datawrapper-height"][a]+"px"}}}))}();</script>  
	

The tunneling effects are now clearly represented. At the origin, the Columb effect forms a cohesive barrier. In the following two slices, you can see the isolated behavior of the degenerative states between the dots! *(probably ;)   

The final eigenvalue graph is likewise successful. I mapped the resultant values in green with the nearest neighbor algorithm to stand out from the existing color scheme.   

<iframe title="D2" aria-label="Interactive line chart" id="D23D" src="/images/projects/Quantum/figures/eval_d2_critical.html" scrolling="no" frameborder="0" style="width: 0; min-width: 200% !important; border: none;" height=1024></iframe>  

<script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(e){if(void 0!==e.data["datawrapper-height"]){var t=document.querySelectorAll("iframe");for(var a in e.data["datawrapper-height"])for(var r=0;r<t.length;r++){if(t[r].contentWindow===e.source)t[r].style.height=e.data["datawrapper-height"][a]+"px"}}}))}();</script>  
	
From a top-down perspective, these isolated values maintain the hole-dot symmetry and form the coordinates for the hexagonal nature of the original diagram.   

As this was an initial exploration and modeling of the behavioral characteristics of this dataset, I will need to conduct further analysis to determine the accuracy of the selected values and implement an efficient pipeline. However, this exercise did succeed in building interactive models that can efficiently communicate behavioral models of fundamental quantum computing systems from a real-world dataset. This process also helped establish a more intuitive understanding of these systems and narrow my focus for projects to be tackled in future efforts.   

_All graphs used in this project can be downloaded from ['/Quantum/figures'](https://github.com/ElishaPhillips/ElishaPhillips.github.io/tree/main/images/projects/Quantum/figures)_

 
[^1]: Zwerver, A. M. J. et al. “Qubits made by advanced semiconductor manufacturing.” (2021).
		[https://arxiv.org/abs/2101.12650v1](https://arxiv.org/abs/2101.12650v1)
	
[^2]: Wiel, Wilfred van der et al. “Electron transport through double quantum dots.” Reviews of Modern Physics 75 (2002): 1-22.						[https://arxiv.org/abs/cond-mat/0205350v2](https://arxiv.org/abs/cond-mat/0205350v2)
	
[^3]: Wang, Xin, Shuo Yang, and S. Das Sarma. "Quantum theory of the charge-stability diagram of semiconductor double-quantum-dot systems." Physical 			Review B 84.11 (2011): 115301.
		[https://arxiv.org/abs/1104.5491v2](https://arxiv.org/abs/1104.5491v2)

	
