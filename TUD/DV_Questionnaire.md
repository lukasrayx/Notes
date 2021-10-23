# **01 – Intro & Foundations**



**Define the term (data) visualization. (1 Pt.)**

Visualization is the process of transforming information into a visual form, enabling users to observe the information

**Describe 2 differences between <u>SciVis and InfoVis</u>. (2 Pt.)**

SciVis is physical data, and spatialization is given. But InfoVis is abstract data, and spatialization is chosen.

**Given a picture of 4 blocks with arrows, (see slide 19) … Complete the <u>visualization pipeline</u>. Write down the appropriate stages. (2 Pt)**

![](https://i.imgur.com/u9AlHcA.jpg)



**Sort the components of the visualization pipeline (write numbers into given blocks, see slide 19)**

待定

**Describe <u>3 important steps</u> in the <u>visualization pipeline</u> (2+2+2 Pt.)**

Data acquisition - Analysis - Visualization

Ref:

![](https://i.imgur.com/zFrIipr.jpg)

**Name and describe 2 of the 3 goals of visualization (2+2 Pt.)**

![](https://i.imgur.com/Z325h0d.jpg)

**Name and describe 2 of the 3 phases of the visualization process (2+2 Pt.)**

如上图

**Describe the differences between Weak Coupling and Strong Coupling in the simulation-visualization process. (2 Pt.)**

（不确定）

Weak Coupling 

Ref:

![image-20210315180407013](/Users/lucas/Library/Application Support/typora-user-images/image-20210315180407013.png)

**Describe a scenario where weak coupling is not feasible. (2 Pt.)**

（没懂）

If the resulting data from simulation is very big, it's more feasible to generate the image on a cluster as well and transmit only the resulting image.

**Describe 3 out of 7 the following general interaction tasks: Overview, zoom, filter, details-on-demand, relate, history, extract (3 Pt.)**

![](https://i.imgur.com/C7Ovy6R.jpg)

**Describe an advanced interaction technique (Overview + Detail, Zooming and Panning, Focus + Context, Brushing and Linking) (2 Pt.)**

![](https://i.imgur.com/DtHyjGC.jpg)

![](https://i.imgur.com/dIML6dH.jpg)

**Given a picture of a bad visualization… Describe 2 problems that makes this visualization a bad one. (2 Pt)**



**Given 2 visualization examples of the same data… Which visualization is better? Describe why. (2 Pt.)**

**Given 3 pictures of basic diagrams… Name the basic diagram types. (3 Pt.)**

**Given 3 pictures of scientific visualizations… Name the visualization methods. (3 Pt.)**

**Sketch the following basic diagram types: bar chart, line chart, pie chart etc. (1 Pt. each)**

**Given a blank table NxM where N are the dimensionalities of the observation space and M are the dimensionalities of the feature space… Fill out the table with own examples, e.g. for N,M=1..3 that means 9 examples (9 Pt.)**

KW: **Data Dimensionality**

![](https://i.imgur.com/DukMR9F.jpg)

**Given examples of simulation data… What is the dimensionality of the observation space? What is the dimensionality of the feature space?**

(see above)

**Given a blank table NxM where N are the dimensionalities of the observation space and M are the dimensionalities of the feature space. Furthermore, given are X examples of data… Put the data in the right cells. (optional: Fill out the remaining empty cells with own examples) (X\*0.5 + N\*M-X Pt)**

(See above)

**Describe the 3 types of <u>area influence</u> that a specific data value can have: reference point, local reference and global reference (3 Pt.)**

- Reference point
- Local reference 
- Global reference

Ref: KW: **Area of Influence, Visalization Rules**

![](https://i.imgur.com/3MS0IaP.jpg)

**Describe how the area of influence (reference point, local reference, global reference) for a given data value should be generally visualized. (3 Pt.)**

(not sure)

Ref:

![](https://i.imgur.com/yulspF3.jpg)

**Name 3 different <u>types of data grids/meshes</u> (3 Pt.)**

KW: Grid/Mesh Type

![](https://i.imgur.com/OBJxAzY.jpg)

![](https://i.imgur.com/DaEiuXf.jpg)

**Given 4 pictures of grids… Name the given grids/meshes. (2 Pt.)**

(See above)

**Sketch one of the given <u>grids</u>: regular, irregular, unstructured, curvilinear (1 Pt.)**

(see above)

**Describe 2 differences between <u>regular and unstructured</u> grids. (2 Pt.)**

(See above)

**Given is diagram of value ranges qualitative (with sub-categories nominal and ordinal) vs. quantitative…Assign the matching properties to the nodes: has metric, has no metric, has order, has no order, discrete, continuous (5 Pt.)**

![](https://i.imgur.com/2nkBY8D.jpg)



**Name an example for each of the following value ranges: nominal, ordinal, metric (3 Pt.)**

- Nominal: name
- Ordinal: thermal feeling
- Metric: temperature

**Given are the 3 data types: scalar, vectorial, tensorial… Assign X examples of data sources to each of the categories. (X*3 Pt.)**

(没懂)

Temperature , density;    position, velocity, acceleration;	stress

**Given are the 3 data types: scalar, vectorial, tensorial and X data sources… Assign the data sources to the right categories. (X*0,5 Pt)**

(待定)

**Given the taxonomy by Shneiderman (slide 50)… Write down an example for a possible data source for each of the elements in the list. (7 Pt.)**

（待定）

**Given the taxonomy by Shneiderman (slide 50) and X examples… Put the given data in the right cells.**

**(optional: Fill out the remaining empty cells with own examples) (X*0.5 + 7-X Pt)**

待定



## **补充**

KW: **Visualization Modes** 

![](https://i.imgur.com/xYKqrrD.jpg)

KW: **Visual Analytics , Visual Data Exploration**

![](https://i.imgur.com/rq2CCYM.jpg)

KW:  **Interaction techniques**

![](https://i.imgur.com/GTADjRp.jpg)

KW: **Data Sources**

![](https://i.imgur.com/YhnPYsN.jpg)

KW: **Data Models**

![](https://i.imgur.com/UyJNth8.jpg)

**Shneiderman, Interaction Tasks**

![](https://i.imgur.com/ltZ5StY.jpg)









# **02 – Perception**

**What does preattentive perception mean? In what period of time does it typically occur?**

Preattentive perception is the subconscious accumulation of information from the environment, without need for focusing attention.

200-250ms qualifies as pre-attentive; 

If a decision takes a fixed amount of time regardless of the number of distractors, it is considered to be preattentive.

If certain elements in a visualization can be perceived without cognitive effort or focussing attention.

Ref:

![](https://i.imgur.com/e7pRQQm.jpg)



**Which visual characteristics can be perceived well preattentively, which less? Give examples of multiple attributes that hinder preattentive perception.**

Color and form can be perceived well preventively 

Which less?: 

multiple attributes examples: 

Ref: kw: preattentive processing

![](https://i.imgur.com/YNHG5ER.jpg)

![](https://i.imgur.com/P6LU99G.jpg)



**Name and explain essential design principles. Establish references to known visualization techniques and explain why observance of the principles is essential. Study well-designed advertising brochures and name the design principles used.**

design principles: (例题如: which diagram is better?)

- figure and ground
- similarity: Similar objects will be perceived as belonging together
  - Size, form, color
  - color groups stronger than form
- proximity: Close objects will be perceived as belonging together 
  -  Proximity stronger than Similarity 
- Connectedness : Even stronger than Similarity (size, color, form) and Proximity 
- symmetry:  Connection of similar objects along symmetric axis 
- closure : Closed contours to show set relationship 
  -  Form does not need to be complete to be perceived as a whole 
  - Humans add remaining bits cognitively 
  - Convex forms are preferred 
- continuity :  Visual entities tend to be smooth and continuous 
  - Also: Smooth Gradient 
  -  Contours are mentally continued so that they do not
    - change direction abruptly 
    -  Introduce new forms
- Relative size
- common fate:  Similarity perceived in dynamic animations
  - Objects moving in the same direction appear to be connected

Why observance is essential:

Ref: kw: Gestalt principles , Max Wertheimer 

![](https://i.imgur.com/kqLy7bm.jpg)

kw: figure/ground

![](https://i.imgur.com/YrP3cSn.jpg)

## 补充:

kw:  Stepwise Processing of Visual Informaiton

![](https://i.imgur.com/vZlu4Ca.jpg)

kw: nonlinear scaling

![](https://i.imgur.com/hdvjCul.jpg)

Kw: stevens's Power Law

![](https://i.imgur.com/zPyDTe0.jpg)





# **03 – Visual Variables**

**Analyze the visual variables used in visualizations (e.g. in journals). Are the visualizations effective? If necessary, find alternative possibilities.**

没懂题目

**Which visual variables can be distinguished in general, and which of them can be assigned to intrinsic固有的 codes?**

Visual variables: <u>2 dimensions + 6 ritinal variables</u>

be assigned to instrinsic codes: shape, texture   **(not sure)**

Ref: visual variables, retinal variables 

![](https://i.imgur.com/zmkPhyU.jpg)

**If you want to visualize <u>quantitative data</u> as <u>exact values</u> or only <u>as tendencies</u>, which visual attributes do you typically use? Justify your decision.**

- as **exact**: position, maybe length, maybe angle/slope
- as **tendency**: angle/slope, area(size), volume, maybe value

![image-20210315230028361](/Users/lucas/Library/Application Support/typora-user-images/image-20210315230028361.png)

For quantitiative data i'd only pick position, because it's the only variable that shows values exactly. For tendencies i'd pick size and value, because relative sizes can be represented by them.



**Bertin identified four basic perceptual questions and a number of visual variables. Which variables are best suited for which type of perception?**

![](https://i.imgur.com/80YxZe6.jpg)

Ref: **perceptual properties, perceptual types**

![](https://i.imgur.com/4qu4lBe.jpg)



**Describe the two design goals of <u>visual mapping</u>, expressiveness and effectiveness. (1+1 Pt)**

Expressiveness: diagram shows exactly the information from the data

Effectiveness: speed with which the view can grasp the information

Ref: kw: **effectiveness maximization, mackinlay**

![](https://i.imgur.com/y4B8eYS.jpg)

**Describe what <u>monosemic encoding</u> means. Why is that an important goal for graphical symbols? (1+1 Pt)**

monosemic means each symbol has a single meaning.

Why important?: 

Ref: kw: **Simiology, monosemic, polysemic**

![](https://i.imgur.com/18Y84ZG.jpg)



**Fill in 3 visual variables and assign the supported perceptual types(use yes/no/partially)**

![](https://i.imgur.com/w2BFSfg.jpg)

Ref: kw: **perception of visual variables, perceptual types**

注: 第一行是Position

![](https://i.imgur.com/mSVJ3ZR.jpg)

**What are the visual variables that support the perceptual types below? For each row, fill in at least 2
variables of the following: position, size, value, texture, color, orientation, shape (4 Pt)** 

![](https://i.imgur.com/yjQWTP3.jpg)

Ref: see above!

**Bertin distinguishes the 4 <u>perceptual types</u> below. Describe each of them in one sentence and give as an**
**example one visual variable that supports the type. (4+2 Pt)**

![](https://i.imgur.com/oTfB14i.jpg)

Ref : see above!

**In the visual mapping process, we define mapping goals at first. Assume the given goal “Which area is the**
**hottest in a weather map?” Describe which of the perceptual types associative, selective, order and/or quantitative is needed to answer the question. (2 Pt)**

Associative and Selective

**Sort the following visual variables by their effectiveness for the given types of data: color hue, length, area**

![](https://i.imgur.com/TUSXfxo.jpg)

Answer :

![](https://i.imgur.com/0JOtKqI.jpg)



**Out of all the following variables, find the (one) visual variable that is the most effective for each of the data types below. (3 Pt) angle, area, color hue, color saturation, connection, density, length, shape, texture, volume**
**Most effective for the data type…**

**a) … quantitative:**  length

**b) … ordinal:**  density

**c) … nominal:**  color hue



**Shortly describe 3 <u>capabilities</u> that can be expressed by the use of color. (3 Pt)**

- Distinction
- Emphasis
- Replica of natural phenomena like temperature
- Expression of mood

Ref: kw: capabilities, mapping to color

![](https://i.imgur.com/3et08Ur.jpg)



**Attention is needed when using color! Describe 2 problems regarding human perception that can occur with color as the visual variable. (2 Pt)**

Ref:  

![](https://i.imgur.com/iyXo10j.jpg)

**To <u>maximize the effectiveness</u> of selective perception, we can make use of the human ability of <u>preattentive processing</u>. With that in mind please describe the method <u>linear separation</u> regarding the selection of colors. Also outline an experimental scenario to test this method. (1+1 Pt)**

Ref: kw: **linear separation**

![](https://i.imgur.com/xbVOLd6.jpg)



**Regarding the design of a color palette that is considered to visualize nominal data we need to ensure equal lightness between each of the colors. In this context, depict the differences between lightness and brightness. (2 Pt)**

Brightness is the absolute visual perception of luminance incorporating all perceptual effects of the human visual system. Brightness increases if the overall illumination is increased.

Lightness, , also known as value or tone , is the relative brightness in a scene and does not change with an increase of the overall illumination.



**Describe a method that can be utilized to <u>produce a color palette</u> of <u>equal lightness.</u> (3 Pt)**  

Fixing a L value yields an equal brightness color palette.

没懂

Ref: kw: equal brightness

![](https://i.imgur.com/WpxMKNR.jpg)



**Regarding color palette design for <u>nominal data</u>, which color space is usually used to <u>maximize linear separation</u>? Describe a method for color palette generation utilizing <u>maximized linear separation</u> in the last-mentioned color space. (1+2 Pt)**

which color space: LUV color space

Method: 

Ref: kw: **Color palette design, nominal data.** 没懂

![](https://i.imgur.com/T4VfOko.jpg)

注：

L表示lightness， 固定了lightness的取值，就可以得到同lightness或者是说brightness的色彩，UV分别代表不同颜色信号



**Describe 3 important design criteria regarding color palette design for <u>quantitative and ordinal data</u>. (3 Pt)**

- Preserve order and for quantitative attributes value differences in perceived colors
- obvious start and end colors
- Obvious changes of the hue should be reserved for critical areas
- Colorblind save

Ref: kw: design criteria

![](https://i.imgur.com/xobyHFa.jpg)



**Given 2 examples of bad color maps… Why are these color maps inappropriate in the context of ordinal data? Shortly describe the issues. (1+1 Pt)**

Ref: see above!



**Shortly describe a method how the perception of ordering in a color map can be improved/achieved. (1 Pt)**

不知道

**Given one example of visualization utilizing <u>bi-variate</u> color scales… Describe what type of color scale was chosen. (1 Pt)**

Ref: kw: bi-variate color scales

![](https://i.imgur.com/fLun9h7.jpg)

**Name 3 texture attributes that can be utilized as visual variables regarding ordinal data. (3 Pt)**

- nominal data
- ordinal data
  - Grain size
  - contrast
  - density
  - regularity
  - Orientation 
- quantitative data : some continuous
  texture attributes available:
  - grain size
  - contrast
  - Orientation 

Ref: kw: **Mapping to texture**

![](https://i.imgur.com/vbvz3c9.jpg)

**Name 2 visual attributes (except position) that textures based on <u>Gabor functions</u> can utilize. (2 Pt)**

- amplitude
- frequency of vibration
- direction of vibration
- Size of gaussian window function

Ref: kw: **Texture Synthesis. Gabor functions**

![](https://i.imgur.com/ZIF67W3.jpg)

**Given example picture of textons… Describe the 3 visual variables that the given Texton Mapping utilizes.**

Ref: kw: Texture Synthesis- Texton Mapping

![](https://i.imgur.com/VwKNBZO.jpg)



**To synthesize合成 a complete texture, the observed data is sampled and the resulting textons are blended additively. Name 2 <u>sampling</u> approaches and describe each of them shortly. (2+2 Pt)**

- Uniform Sampling: 
- Inverse Area Sampling:
- Poisson Disk Sampling:

Ref: kw: **Texture Synthesis- Sampling**

![](https://i.imgur.com/NYsqvfC.jpg)



## 补充：

kw: **mapping goals and guidelines, associative, selective**

![](https://i.imgur.com/4nC2B6i.jpg)

Kw: **describe how light**

![](https://i.imgur.com/oeodCul.jpg)

Kw: **design goals , color palette design**

![](https://i.imgur.com/PehStPO.jpg)

kw: **quantitative and ordinal data, transfer function, color scale**

![](https://i.imgur.com/ZFTUFjH.jpg)







# **04 – Attribute Visualization / Multivariate Data**

**Select examples of data objects with <u>1-n attributes</u> and consider which visualization forms are suitable for comparison, analysis or search tasks. For <u>multivariate data</u>, try to identify primary or dominant attributes.**

![](https://i.imgur.com/i7W7IRq.jpg)



**In which of the <u>visualization forms</u> discussed in the lecture can correlations in 
a) <u>static state</u> and 
b) <u>dynamic</u> (i.e. <u>through interaction</u>) be identified?**

a) star plot sactterplot

b) linked histograms, 3D scatterplots, parallel coordinates

**Why are <u>scatterplots</u> such a frequently used visualization form? For which data types and visualization tasks are they suitable? Which extension possibilities do you know?**

they are expressive; for two quantitative value attributes; find trends, outliers, distribution, correlation; with color and/or size encodings.

Extension: color/size encoding

**Name, describe, and compare visualization techniques for <u>trivariate data</u>.**

linked histograms, extended scatterplots, scatterplot matrix, 3D scatterplot 

Scatterplot + Visual Attribute (Extended Scatterplot) - a normal scatterplot with a x and y axis and for the third attribute we can use color or size encoding 3D Scatterplot - a Scatterplot with 3 axis, x, y and z. Comparing with the Extended Scatterplot it has problems to understand correlation, interaction is necessary to improve 3D Scatterplot Scatterplot Matrix - projects the 3 axis areas and it can compare objects with regard to any attribute combination, but comparing with the other two visualization techniques every object appears 3 times and it doesn't have much space for labels.

**How can visualization techniques for <u>multivariate data</u> be categorized in principle? Name examples.**

<u>Geometric mapping/geometric representation</u>:

*Non-orthogonal axes: parallel coordinates, star plot Multiple views: plot matrices, brushing histograms Semantic mapping/iconic representation:*

<u>Complex glyphs</u>: 

*Chernov faces, embedded visualisations*

**What is the core idea of the <u>Parallel Coordinates</u> technique, and which <u>inherent problem</u> is elegantly solved with it? Say something about the complexity of this technique.**

Core idea:

inherent problem:

Complexity:



Ref:

![](https://i.imgur.com/kSFwGij.jpg)



**Distinguish attribute and object visibility for <u>multivariate data</u> visualizations and give examples for each group.**

![](https://i.imgur.com/GV37BKp.jpg)

Ref:  KW: **object visibility / attribute visibility** / **dimentional visibility**

![](https://i.imgur.com/2x21aoo.jpg)

![](https://i.imgur.com/TuoqXLD.jpg)



**Why do <u>parallel coordinates</u> hardly support <u>object visibility</u>, but <u>attribute visibility</u>?**

Because attributes are plotted on parallel axes, hard to get idea of whole object layout with so many lines crossing each other.



## 补充：

kw: core data types

![](https://i.imgur.com/NUzQQb8.jpg)

![](https://i.imgur.com/E7qkh5E.jpg)

kw: **scatterplot, visual attribute, overplotting**

![image-20210316132635003](/Users/lucas/Library/Application Support/typora-user-images/image-20210316132635003.png)

 Kw: 3d-scatterplot, spin plot

![image-20210316132747063](/Users/lucas/Library/Application Support/typora-user-images/image-20210316132747063.png)

kw: scatterplot matrix

![image-20210316132812022](/Users/lucas/Library/Application Support/typora-user-images/image-20210316132812022.png)

Kw: linked histograms(dynamic)

![](https://i.imgur.com/zTn2XOU.jpg)

kw: star plots

![image-20210316134044631](/Users/lucas/Library/Application Support/typora-user-images/image-20210316134044631.png)

kw: n-d Space to 2D Screen

![](https://i.imgur.com/MfLXNW5.jpg)







# **05 – Visualizing Relations**

**Why do <u>lines</u> play an important role in many forms of representation of relations? Name key techniques that make effective use of lines.**

why?: Simplest and often most effective method to connect two items.

usage: often used for tree and graph visualizations

Ref:

![](https://i.imgur.com/gcMJmWG.jpg)

**Explain and contrast the <u>quantity-oriented diagram</u> visualization types <u>Venn diagram</u>, <u>InfoCrystal</u> and <u>ClusterMaps</u> with a self-chosen example.**

All useful for analysing clusters and aggregations in data with few attributes.

Venn diagram 2-3 / InfoCrystal 3 / ClusterMaps 2 - circa 9 attributes

All have scalability issues as data becomes hard to read

Example: ?  



**Which essential aspects and challenges for graph visualizations are known to you? **

![](https://i.imgur.com/fpxkwZF.jpg)



**Explain at least 5 guidelines for drawing graphs. How can we group the rules?**

待定

**Select sample diagrams and check the extent to which Moody's rules have been taken into account.**

待定

**Name and describe basic graph layout techniques and explain which aspects have been well solved and which problems exist.**

待定

**Also discuss 3D solutions or hyperbolic representations and their potential.**

待定

**Set up an overview of all <u>tree visualizations</u> you learned in the lecture. Select three sufficiently different ones and explain these techniques in detail.**

- simple indentations
- node-link diagrams
- space filling approaches
- layered approaches

Ref:kw: **tree visualization**

![](https://i.imgur.com/dWzMtQi.jpg)

![](https://i.imgur.com/ZT6pkwz.jpg)

![](https://i.imgur.com/Aw4zIkT.jpg)



**How can <u>tree visualizations</u> basically be grouped and structured?**

Simple indentations 凹口, node-link diagrams (networks), space filling approaches (enclosure), layered approaches

Ref: see above!



**What is the main difference between <u>Node-Link Diagrams</u> and <u>Enclosure Diagrams</u>? Give examples from each category and explain advantages and disadvantages in terms of usability.**

![](https://i.imgur.com/YAYt150.jpg)



**Select a folder on your hard drive (which contains neither too many nor too few subfolders and files) and <u>construct a treemap</u>. You can also write your own program or follow the algorithm of an InfoVis toolkit.**

待定 X

**Use examples to explain where the <u>limits of using 3D graphics</u> lie and why metaphors taken too literally do not necessarily have to be advantageous.**

Occlusion, scalability, traversability are all problems with 3D visualizations

**Think about the role of the visual repertoire or the grammar of visual diagram elements using self-chosen examples. For example, pick out some of the tree visualization techniques presented and consider how they could be improved visually.**

待定



## 补充

Kw: graphs and trees

![image-20210316145053564](/Users/lucas/Library/Application Support/typora-user-images/image-20210316145053564.png)

kw: **node link diagrams**

![](https://i.imgur.com/lg2LpjY.jpg)

![](https://i.imgur.com/GZaUEsg.jpg)

Kw: **space filling hierarchies**

![image-20210316150752643](/Users/lucas/Library/Application Support/typora-user-images/image-20210316150752643.png)

![image-20210316150837118](/Users/lucas/Library/Application Support/typora-user-images/image-20210316150837118.png)

![image-20210316150845614](/Users/lucas/Library/Application Support/typora-user-images/image-20210316150845614.png)

Kw: **layered approaches**, decoupling structure

- Icicle trees
- Sunburst 
- facetZoom

![](https://i.imgur.com/s5T8PL0.jpg)

![](https://i.imgur.com/S2JfPzn.jpg)

Kw : **3D tree** 

![](https://i.imgur.com/Q7a9a7j.jpg)

![](https://i.imgur.com/jbojK3J.jpg)

![](https://i.imgur.com/AVY4Itw.jpg)

![](https://i.imgur.com/KerihRw.jpg)

![](https://i.imgur.com/yJ9jtJD.jpg)

kw: **force-directed placement**

![](https://i.imgur.com/3W40ga5.jpg)

kw: **multilevel networks**

![](https://i.imgur.com/FZFBwMv.jpg)

kw: **adjacency matrix views**

![](https://i.imgur.com/vjZorY0.jpg)

![](https://i.imgur.com/vDHA5Yw.jpg)

kw: **tamara Munzner's View**

![](https://i.imgur.com/GGfIaRW.jpg)







# **06 – Time Visualization**

**Which temporal aspects of data can be distinguished?**

kw: **characteristics of time-oriented data**

![](https://i.imgur.com/2vqjSIO.jpg)

Ref: slide07(p7-10)

**Name several example techniques for each <u>time visualization</u> group and explain one representative in detail.**

待定

**How well can periodic relationships of events be read with a <u>Gantt or Pert-diagram</u>?**

Gantt: Possible to see

Pert: Poorly visible



**Explain examples for the <u>use of axes</u> for time and other variables and describe possibilities <u>how such axes</u> can be combined. What are the <u>advantages and disadvantages</u>?**

待定

**Give an example and the advantages and disadvantages of <u>radial time visualizations</u>.**

待定

**Choose possible dimensions for a <u>taxonomy of time visualization</u> techniques that you consider important (why?) and develop your own classification scheme.**

待定



## 补充：

Kw: **Mapping time-oriented data**

![](https://i.imgur.com/3iQleaS.jpg)











# **07 – Presentation and Interaction**

**Name one possible <u>classification</u> for data analysis tasks. Why do tasks play a crucial rule?**

Classification:

Why:

Ref:

![](https://i.imgur.com/MIjXyrJ.jpg)



**What are <u>multiple coordinated view</u>s? Explain the concept and discuss advantages for data exploration.**

what: combine multiple types of view on the same visualization. 

Advantages: It allows the discovery and perception of relations or the use of further concepts like focus and context.

**Name examples for the combination of different presentation techniques that allow displaying large data amounts on small displays and keeping an overview in detail views.**

Example VisTiles: Coordinating and Combining Co-located Mobile Devices for Visual Data Exploration

**Define and characterize <u>zooming & panning</u>.**

Ref: kw: **zooming and panning**

![](https://i.imgur.com/vpcGL1A.jpg)



**Explain the concepts of geometric zoom and semantic zoom.**

![](https://i.imgur.com/hJ49k0E.jpg)



**When using zooming and panning in combination, which issues can occur?**

Temporary loss of contextual information

**Explain and characterize <u>space-scale diagrams</u> (SSD) and describe different possible pan-zoom trajectories.**

Analytical system for understanding of ultiscale spaces/UIs

Ref:

![](https://i.imgur.com/HT4k7mI.jpg)

**Explain different possible <u>zoom effects</u> by using a <u>space-scale diagram</u>.**

Ref: **zoom-effects, semantic zooming and zoom effects**

![](https://i.imgur.com/SUMBqCq.jpg)

**What is Speed-Dependent Automatic Zooming? For what is it used and what are advantages?**

![](https://i.imgur.com/BDkNyba.jpg)

**Select an application that you use often. Reflect in which way the software incorporates techniques such as zooming, focus+context, overview+detail. What additional functionalities would you find helpful?**

待定



**Explain the mathematical functions that allow to describe <u>distortion-oriented</u> focus+context techniques. Name specific examples that were discussed in the lecture.**

Magnification function & Transformation function. Table Lens, Bifocal Display, Polyfocal Display

Ref:

![](https://i.imgur.com/O87Pp3k.jpg)





**Select two <u>distortion-oriented</u> techniques and explain them in detail. Also discuss <u>advantages and disadvantages</u>.**

Perspective wall: uses 3d perspective to increase viewable data. Importance of peripheral data decreases with distance.

Fisheye view: Data in center of domain gets increased importance. Grid is heavily distorted in an irregular way. Peripheral data is hard to read.



**What is the main difference between Bifocal Display and Perspective Wall?**

Importance of peripheral data decreases with distance

**Provide the transformation function and the magnification function for Bifocal Display and Graphical Fisheye Views.**

![](https://i.imgur.com/hMsljqP.jpg)

![](https://i.imgur.com/0rgVcMk.jpg)



**Explain a possible classification of distortion-oriented techniques based on the magnification.**

Non-continuous vs. continuous magnification functions

Ref: kw: **Taxonomy Distortion-oriented Methods**

![](https://i.imgur.com/BSVaRle.jpg)



## 补充：

kw: **Large Graph Analysis**

![](https://i.imgur.com/jWNqb2E.jpg)

kw: **large information spaces**

![](https://i.imgur.com/CzTng9Z.jpg)

kw: **Focus and context**

- Cue Methods
- Spatial Methods : show everything at once in the same plane but show some parts in more detail
- Dimensional Methods

![](https://i.imgur.com/LhhwYoK.jpg)

kw: **Cue Methods**

![](https://i.imgur.com/16GYEsi.jpg)

![](https://i.imgur.com/H670pfA.jpg)

Kw: **Spatial Methods**

![](https://i.imgur.com/gHuta65.jpg)

![](https://i.imgur.com/Xq7Pdg7.jpg)

Kw: **Bifocal Display**

![](https://i.imgur.com/x6gaDqq.jpg)

kw: **Polyfocal Display**

![](https://i.imgur.com/5ECqEG3.jpg)

![](https://i.imgur.com/KqcdzBe.jpg)

![](https://i.imgur.com/DvaVIYG.jpg)

![](https://i.imgur.com/Ic5xsuZ.jpg)

![](https://i.imgur.com/Li14vgI.jpg)

Kw: **Spatial Methods- Distortion-oriented: Perspective Wall**

![](https://i.imgur.com/k3gSU1v.jpg)

![](https://i.imgur.com/otsi1qN.jpg)



# **08 – Introduction to Scientific Visualization**

**Describe all the parts of a typical scene required for <u>3D rendering</u> on a graphics card. (4 Pt)**

- 3D models
- Light sources
- Camera
- Scene

Ref: **3D Rendering, 3D Scene description**

![](https://i.imgur.com/cu9N58d.jpg)

**In <u>3D scenes</u>, meshes are often used to describe shape and visual appearance. In this context, please shortly describe the following attributes that a vertex of a <u>3D model</u> can have: position, color, normal, texture coordinates (4 Pt) **

Ref: kw: **3D Models**

![](https://i.imgur.com/BlKIvos.jpg)



**Describe the following surface definitions (+advantages/disadvantages?): <u>triangle mesh</u>, <u>parametric surface</u>, <u>height field</u>, <u>iso-surface</u> (8 Pt)**

**triangle mesh**:  It comprises a set of triangles (typically in three dimensions) that are connected by their common edges or corners.

Parametric surface: A **parametric surface** is a **surface** in the Euclidean space which is defined by a **parametric** equation with two parameters. . **Parametric** representation is a very general way to specify a **surface**, as well as implicit representation.

Height field: In computer graphics, a heightmap or heightfield is a raster image used mainly as Discrete Global Grid in secondary elevation modeling. Each pixel stores values, such as surface elevation data, for display in 3D computer graphics.

Iso-surface: An **isosurface** is a three-dimensional analog of an isoline. It is a **surface** that represents points of a constant value (e.g. pressure, temperature, velocity, density) within a volume of space; in other words, it is a level set of a continuous function whose domain is 3D-space.

- Isosurface is sometimes used more generically related to domains of more than 3 dimensions.

Ref: **3D Models**

![](https://i.imgur.com/4SUZw3o.jpg)



**How can one compute the normal of an iso-surface? (2 Pt)**

derivative over normalized length

**Describe 2 different types of <u>light sources</u> and draw a sketch for each in the given field.**

- Directional light source
- Point light source

![](https://i.imgur.com/bpxp2nY.jpg)



**What is needed to define a simple model of a <u>pinhole camera</u>? Name the required internal and external parameters/variables. (1+1 Pt)**

Internal parameters: 

- pixel resolution of sensor in x and y direction, 
- opening angle, 
- distance of far and near clipping 

External parameters: 

- eye and pinhole location, 
- view-direction and view-up-direction

注：Pinhole: 小孔

![](https://i.imgur.com/KIxoh7p.jpg)



**Describe the term <u>view frustum</u>. (2 Pt)**

Visible part of the scene, described by far and near clipping plane and the sensor edges

**Which mathematical structures are used to provide <u>3D model transformations</u>? How are they used? (2 Pt)**

**which**: Matrix-vector-multiplications.

 **usage**: Used for transformation of positions and normals

Ref:

![](https://i.imgur.com/FEGwH62.jpg)



**What is the advantage of using <u>homogenous</u> vector and matrix representations regarding 3D transformations. (2 Pt)**

Can be transformed by Homogeneous Transformation Matrices which describe both Rotation and Translation in 3D Euclidean space.

**Given the picture from slide 19… Given is the sequence of steps in the <u>rendering process</u> from a scene object with its <u>vertex positions</u> in object coordinates to the rendering-ready positions in window coordinates. Fill out the remaining fields. (5 Pt)**

Ref: kw: transformations- modelview, projection, and viewport

![](https://i.imgur.com/711PSwC.jpg)

![](https://i.imgur.com/GVmXpId.jpg)



**What are the main shader units in a modern <u>OpenGL</u> pipeline? (1.5 Pt)**

- vertex shader, 
- geometry shader, 
- fragment (or pixel) shader

Ref: 下图绿色框内

**Shortly describe how the data is transferred from the CPU to the GPU and how the data is processed afterwards. (2+4 Pt)**

Ref: kw: **rendering pipeline,  draw-calls data**

![](https://i.imgur.com/ONQslHG.jpg)

**Given a picture as on slide 21 (eye, light source, surface point, surface normal)… Depict the variables and parameters that are required for basic lighting calculations. (2 Pt)**

𝝎in, normal, 𝑳in

Ref：kw: surface appearance, diffuse reflection, reflection model, lighting calculations

![](https://i.imgur.com/zybPp0j.jpg)



**Given pictures of spheres with different lighting models (ambient only, Lambertian, Blinn, combined)…Assign the following light models to the pictures: No lighting, Lambertian reflectance, Specular BlinnPhong, Lambertian and Blinn-Phong combined (3 Pt)**

![](https://i.imgur.com/0xChYyD.jpg)



**In the rendering process, the primitives are processed in the order of their occurrence. Usually they are not sorted by visibility. To establish the right depth order one could utilize the <u>z-buffer</u> method. Please describe this approach. (4 Pt)**

**z-Buffer**: A **depth buffer**, also known as a **z**-**buffer**, is a type of data **buffer** used in computer graphics used to <u>represent **depth** information of objects in 3D space</u> from a particular perspective. **Depth buffers** are an aid to rendering a scene to ensure that the correct polygons properly occlude other polygons.

Ref； KW: visibility sorting / z-buffer / depth test

![](https://i.imgur.com/pWZaOsh.jpg)

**Regarding <u>transparency</u>, describe how <u>visibility sorting</u> can be done on fragment level. (3 Pt)**

Ref: 

![](https://i.imgur.com/DXmItjE.jpg)



**Shortly describe back-to-front rendering and, in this context, the over operator. (1+2 Pt)**

Fragment colors are blended in visibility order with the over operator 𝒄over= 𝛼front𝒄front + (1−𝛼front) 𝒄back



**A small boundary around semi-transparent objects can improve the visual perception. What is the Name of this techniques? (1 Pt)**

Ref: transparent boundary, halo, antialiasing

![](https://i.imgur.com/w6LLHC7.jpg)



**Describe the technique halo. What are the advantages regarding the visual perception of semi-transparent objects. (2+1 Pt)**

Ref: see above!



**Regarding the visualization of 2D scalar fields as pixel images, there are different approaches to optimally map the value range of the data onto the maximum range of the color model values. One of those techniques is called window transfer function. Describe this method with the help of a typical application scenario. (3 Pt)**

Ref:

![](https://i.imgur.com/xQ1jv4U.jpg)



**Regarding the visualization of 2D scalar fields as pixel images, there are different approaches to adapt the value range of the color space to the human visual perception. In this context, describe the technique gamma correction. (2 Pt)**

![](https://i.imgur.com/IWwOJYh.jpg)



**Describe the technique Histogram Equalization. What type of the human visual perception does it utilize?**

![](https://i.imgur.com/oHYRjkS.jpg)



**How can one produce color bands for given 2D scalar data? (1 Pt)**

![](https://i.imgur.com/KmxFLv9.jpg)

**Regarding 2D scalar data, describe the different approaches contour lines and color bands. (2 Pt)**

Ref: see above!

**In 3D domains, there usually is a lot of occlusion. Describe each of the following techniques that counteract this problem: selection, projection, slicing, clipping (4 Pt)**

![](https://i.imgur.com/CpCw8xY.jpg)



**Given pictures of slicing, projection and clipping… Assign the right techniques to the pictures. (2 Pt)**

Ref: see above!



**Describe the technique <u>contouring</u>. How can contouring enrich the representation of a height field? (2+1 Pt)**

What:

How:

clearly delineate and stress contours for data at certain heights for easier reading.

![](https://i.imgur.com/HMKBjJh.jpg)



**Name the techniques that extract iso-lines (2D domain) and iso-surfaces (3D domain). (1+1 Pt)**

contouring -> Marching Squares / Marching Cubes



**How can you compute the surface normals of an iso-surface? (1 Pt)**

(see above): from the (negated) gradient

**Given a picture of a grid cell… Describe the technique Marching Squares. What is the input, the output and the steps that are processed? Complete the sketch. (5+1 Pt)**

Ref:

![](https://i.imgur.com/6aeV5Zp.jpg)

**Given a grid cell processed by Marching Squares that has an ambiguous case… Describe why there is an ambiguous case here and how the ambiguity can be resolved. Use the sketch to support your explanations. (1+2+1 Pt)**

![image-20210316015819863](/Users/lucas/Library/Application Support/typora-user-images/image-20210316015819863.png)

![](https://i.imgur.com/VDaXwMT.jpg)



## 补充：





# **09 – Data Preparation**

**What is the difference between interpolation and approximation? (1 Pt)**

Interpolation fits a function to data in algorithmic/machine precision, whereas 

approximation yields a function that minimizes error in regard to a certain loss function (=norm).

Ref:

![](https://i.imgur.com/S7w2Pqw.jpg)

**Given a picture of an interpolated and an approximated 1D signal… Name the two different techniques with which the <u>signal was reconstructed</u>. Shortly describe them. (1+2 Pt) **

Interpolation: find (often polynomial) function that is sufficient for all collocation points 

Approximation: find function that minimizes the loss function

**Given a grid with grid size Δ𝑥 and a query point 𝑥… Determine the cell 𝑗 𝑥 𝑗 𝑦 and the relative position ( ) within the cell for the query point 𝑥. (2 Pt)**

Ref: kw: point Localization, cell-based interpolation

![](https://i.imgur.com/rMZcNXY.jpg)





**Explain <u>1D linear interpolation</u>. Why is the interpolation problem solved “automatically”? (2+1 Pt)**

because hat functions are 0 for all but the reference sample point

The problem is solved automatically, because the hat functions don’t overlap

Ref:

![](https://i.imgur.com/lTT4Ujj.jpg)

**Given one cell of a grid (with grid size Δ𝑥) and a query point 𝑥… Determine the value of 𝑥 via bilinear interpolation. (2 Pt)**

Ref: kw: 2D Bilinear Interpolation

![](https://i.imgur.com/pUIzgUB.jpg)

**Describe the term affine combination. Which mathematical properties are required? (1+2 Pt)**

Ref: kw: barycentric, Unstructured grids, affine combination simplex

![](https://i.imgur.com/fO9QOhd.jpg)

**What is affine independency? (1 Pt)**

Ref: see above!

**What is the maximum number of independent points in ℝ 𝑑 ? (1 Pt)**

d+1

Ref: see above!

**What is a simplex? (2 Pt)**

Set of d + 1 affine independent points

Ref: see above!



**What are barycentric coordinates? (1 Pt)**

Set of the coefficients of an affine combination of points

Ref: See above!

**Given a picture of a triangle mesh, a target point and a triangle as starting point… Describe an algorithm how to find the triangle that contains the given target point 𝑥 starting with the marked triangle. Please mark the other triangles in the sketch that get visited by the algorithm in the correct order. (2+1 Pt)**

![image-20210316020451169](/Users/lucas/Library/Application Support/typora-user-images/image-20210316020451169.png)



**Regarding a triangle 𝑥 1 𝑥 2 𝑥 3 , describe a method to check whether a point 𝑥 is outside (or inside) of a ( ) triangle edge. (2 Pt)**

![](https://i.imgur.com/oEoXnCo.jpg)



**How can you estimate derivatives in cell-based data? Describe the two techniques forward difference and central difference. (2 Pt)**

![](https://i.imgur.com/wvoZCtC.jpg)



**Describe a case where the results of the central differences deviate strongly from those of the forward differences. (2 Pt)**

for smaller Δxi-1, Δxi (grid spacing),f when function is less smooth. When they are not equidistant, which means Δx != Δxi != Δxi-1

**In contrast to finite differences what is special about the Sobel Operator regarding the quality of the derivatives. (2 Pt)**

Sobel operator combines derivative filter with Gaussian smoothing kernel, resulting in less noisy and more rotational invariant results

**Given pictures of the same data where different approaches for the computation of the surface normal were used… The images were rendered using different methods for normal estimation. Assign the following techniques: forward differences, central differences, Sobel Operator (2 Pt)**

![](https://i.imgur.com/Y1wxbHE.jpg)



**Given a set of points… Draw the Voronoi Diagram for the given set of points. (2 Pt)**

Ref: kw: voronoi

![image-20210316020702751](/Users/lucas/Library/Application Support/typora-user-images/image-20210316020702751.png)

**Describe how a Voronoi Diagram is defined mathematically. (2 Pt)**





**How is the <u>Delaunay Graph</u> generated from a Voronoi Diagram? (2 Pt)**

![](https://i.imgur.com/7EqaRiG.jpg)

kw: Delaunay triangulation- preliminaries , circumcircle外接圆, locally delaunay

![](https://i.imgur.com/Ni8sa8d.jpg)



**Given a Voronoi Diagram… Draw the corresponding Delaunay Graph for the given Voronoi Diagram.**

**Regarding Delaunay Triangulation, describe the Edge-Flipping algorithm. (4 Pt)**

Ref: kw: Edge flipping

![](https://i.imgur.com/FfbfVFW.jpg)

**Given different interpolation approaches… Shortly describe the following interpolation approaches in one sentence and make a statement about the continuity of the functions: e.g. constant on Voronoi Cells, Shepard interpolation, Delaunay triangulation, Natural Neighbour Interpolation (2 Pt each)**

![](https://i.imgur.com/gTyognx.jpg)

**To solve the interpolation problem via Shepard Interpolation, radial basis functions are used. What is a radial basis function? What are advantages and disadvantages of this approach? (1+2 Pt)**

![image-20210316020907270](/Users/lucas/Library/Application Support/typora-user-images/image-20210316020907270.png)



## 补充：

kw: Insertion algorithm, local flips, convex hull

![](https://i.imgur.com/aoqUs4t.jpg)

![](https://i.imgur.com/KGexSFQ.jpg)

**Sobel Operatior**

Central differences is a first-order differential operator for edge detection, which uses the gray difference between the upper and lower, left and right neighbors of a pixel point to reach the extreme value at the edge to detect the edge and remove part of the pseudo-edge. To detect edges by central differencing, the direction of differencing must be perpendicular to the edge direction, which requires differencing operations in different directions of the image, increasing the tediousness of the actual operation.



The Sobel operator considers that the pixels in the neighborhood do not have an equal impact on the current pixel, so pixels at different distances have different weights and produce different impacts on the operator results. In general, the more distant the distance, the less influence is produced.

Sobel is more rotational invariant than central differences

![image-20210317085415447](/Users/lucas/Library/Application Support/typora-user-images/image-20210317085415447.png)

central differences:

* Df/dx = -0.5(normalized: -0.451)
* Df/dy = -0.75(normalized: -0.676)

Sobel

* dy/dx = -0.5(normalized: xxx)
* dy/dx = 01.0 (normalized: xxx)







# **10 – Volume Visualization**

**Motivation:**

![](https://i.imgur.com/L1OMICP.jpg)

**Data Specification**

Kw: grid types

![](https://i.imgur.com/ujfNyLP.jpg)

**Voxel Grid**

![](https://i.imgur.com/XL3dxQl.jpg)



**Compare <u>direct and indirect volume visualization</u>. What are the basic approaches? What are the general differences? (2+2 Pt)**

![](https://i.imgur.com/OQnK6A8.jpg)

**Segmentation/Labeling**

![](https://i.imgur.com/cHfNpYu.jpg)





**What is Oblique Slicing? Describe a CPU and a GPU approach for rendering oblique slices via 3D texture.**

![](https://i.imgur.com/u1osU98.jpg)

![image-20210316021325330](/Users/lucas/Library/Application Support/typora-user-images/image-20210316021325330.png)

**Contouring**

- Cuberille
- Dual Contouring
- Marching Cubes
- Marching cubes with short edges collapsed

![](https://i.imgur.com/01GSFN3.jpg)



**Describe the technique <u>Dual Contouring</u>. (3 Pt)**

![](https://i.imgur.com/PAIXF9E.jpg)



**Describe the Marching Cubes algorithm with the help of a sketch. (3 Pt)**

![](https://i.imgur.com/tPxeGeg.jpg)



**Given a picture of a 3D grid cell and an iso-value 𝑣… Classify the voxel of the cell based on the iso-value 𝑣 and draw the resulting iso-surface intersection points onto the edges. (1+1 Pt)**

**Regarding the Marching Cubes algorithm, how many cases exist (without exploiting symmetries)? (1 Pt)**



**A common problem with marching cubes is that because of the creation of triangles with very short edges, an extremely high number of triangles can be produced. Describe a solution for that issue. (1 Pt)**

![](https://i.imgur.com/f0jfXRt.jpg)

**Describe another technique to reduce the number of generated triangles produced by Marching Cubes. (1 Pt)**

**Describe the basic procedure for direct volume visualization. Consider the terms ray, sampling and compositing. (3 Pt)**

![](https://i.imgur.com/w7UaC4D.jpg)

**Given pictures of different compositing methods for direct volume rendering… Assign the following compositing methods for direct volume rendering to the pictures: max, average, first (2 Pt)**

![](https://i.imgur.com/VANrMDY.jpg)



**Shortly describe the following compositing methods for direct volume rendering: max, average, first (1+1+1 Pt)**

**What is the emission-absorption model and how does the compositing mode blending generally works?**

![](https://i.imgur.com/XKaajnb.jpg)

**What are the two basic parameters controlled by a transfer function? (0.5+0.5 Pt)**

Emission intensity 

Absorption probability

![](https://i.imgur.com/d3t58fW.jpg)

**What are the typical tools of a transfer function editor? (3 Pt) **

Interpolation control, Labeling, (Re-)scaling, Data value manipulation, Color transfer

**What is the purpose of a histogram when designing a <u>transfer function</u>? (1 Pt)**

It allows for multidimensional transfer functions.

![](https://i.imgur.com/VHj8pHX.jpg)

**Given a table direct vs. indirect <u>volume rendering</u> methods… Assign the following techniques to either direct or indirect volume rendering: e.g. texture slicing, shear warp, raycasting, dual contouring, marching cubes, cuberille (0.5 Pt each)**

![](https://i.imgur.com/gvX029b.jpg)

**How can you utilize the shader units on a GPU for raycasting? (3 Pt)**

by sampling view ray for each pixel covered by volume box



**Name and shortly describe two acceleration techniques for raycasting. (1+2 Pt)**

**Empty space skipping:** 

exploit sparse parts 

**Early ray termination:** 

check accumulated opacity and don’t proceed above threshold 

**Sampling rate adjustment:**

homogeneity acceleration: check for gradient - if gradient is low (homogenous region), a lower sampling rate is possible compared to dynamic regions beta-acceleration: higher accumulated opacity -> smaller sampling rate (related to early ray termination)

Ref:

![](https://i.imgur.com/O3Y1jNJ.jpg)



# **11 – Flow Visualization**

**Shortly name and describe the types of local properties that exist in flow data? (1+2 Pt)**

kw； point properties, local properties

![](https://i.imgur.com/t05i8oL.jpg)



**What is a common mathematical approach to analyze the local environment of critical points? (2 Pt)**

Analyse Jacobian of vector field evaluated at the point -> Eigenvalues for stability analysis (attractor/saddle/repelling), rotation

![](https://i.imgur.com/ajNMyge.jpg)



**Given a picture of flow field with marked spots… Describe properties of the critical points marked in the given picture with the following attributes: divergent, convergent, saddle, left/right turning spiral (1Pt each)**

see above

**Name 3 types of characteristic lines in vector field visualization. (1.5 Pt)**

![](https://i.imgur.com/nvplJNm.jpg)



**Characteristic lines are a common approach to visualize vector fields. Shortly describe the following types of lines: stream lines, path lines, streak lines, time lines (4 Pt)**

![](https://i.imgur.com/aKiLyPW.jpg)



**Given pictures of a simulated discrete vector field (see slide 14)… Depicted is the progressive flow field in successive time steps 𝑡 0 . . 𝑡 3 Draw the following characteristic lines in the sketches below: streak line, path line, stream line for 𝑡 2 (3 Pt)**



**Streamlines can be computed by numerical integration. What is a general issue in low order polygonal approximation techniques like the explicit Euler method? (1 Pt)**

![](https://i.imgur.com/iXr9xrS.jpg)



**Shortly describe the technique Integrate and Draw. (3 Pt)**

![](https://i.imgur.com/tLRmAca.jpg)



**How can you extend Integrate and Draw methods to visualize the strength and orientation of the vector field at a given sample position? (1 Pt)**

![](https://i.imgur.com/MZgbcbK.jpg)



**Shortly describe the technique Line Integral Convolution. (3 Pt)**



**Compare the approaches Integrate and Draw and Line Integral Convolution. What are the similarities and what are the differences? (4 Pt)**

![](https://i.imgur.com/1IqcuxA.jpg)



























