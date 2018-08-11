# Open Data ScienceEast (2016)

## Conference Details

Location: Boston, MA
Dates: May 20-22, 2016
URL: https://www.odsc.com/boston

## Speaker Notes

### DAY 1

**A. Open Health Data**

- think of JSON as the "CSV for the Internet Era"
- ```seaborn``` library in Python for dataviz

**B. Keynote: Stefan Karpinski**

- speaker: [Stefan Karpinski](http://karpinski.org/)
- [numFocus](http://www.numfocus.org/)
- [Ousterhout's dichotomy](https://en.wikipedia.org/wiki/Ousterhout%27s_dichotomy):
	- high-level programming languages are either "system programming" or "scripting" languages
- a common two-language compromise:
	- R/Python for scripting
	- C/C++ for "hard stuff"
- two-language problem creates a social barrier - a wall between users & developers
- [Julia](http://julialang.org/) --> low-level & high-level code in the same language

**C. Keynote: Dr. Ingo Mierswa (rapidMiner)**

- speaker: [Ingo Mierswa](http://www.kdnuggets.com/2014/06/interview-ingo-mierswa-rapidminer-analytics-turning-points.html)
- problems:
	- no operalization of models
	- data science takes too long & is too complex
- how do you turn results into business *action*?
- Hadoop as "very complex infrastructure"
- rapidMiner is freen, open

**D. Keynote: Kirk Borne**

- speaker: [Kirk Borne data ethics course](http://kirkborne.net/cds151/)
- "every person is a scientist...testing the world"
- "IBM Scout" app for the NBA
- "absence of evidence is not evidence of absence"
- "the two most important things in data science are the data and the science"

**E. Keynote: Lukas Biewald (CrowdFlower)**

- speaker: [Lukas Biewald](https://en.wikipedia.org/wiki/Lukas_Biewald)
- crowd-sourced data
- just getting more data can improve your model!
	- "the real world is not a Kaggle competition"
- "average analysis on great data can still be useful"
- "an 80% model is useful if you deploy it in areas where it works"
	- weak models are still valuable if you can at least identify specific regions where the model does/does not work
	- ML good @ assessing confidence
- [active learning](https://en.wikipedia.org/wiki/Active_learning_(machine_learning)) - feedback in machine learning from human-in-the-loop
- USPS used OCR as early as 1982
	- with human in the loop + active learning, they get better with every mistake
	
**F. Notebooks with R Markdown**

- speaker: [JJ Allaire](https://en.wikipedia.org/wiki/Joseph_J._Allaire)
- packages:
	- [bookdown](https://bookdown.org/yihui/bookdown/)
	- [flexdashboard](http://rmarkdown.rstudio.com/flexdashboard/)
	- [rboken/Bokeh](http://hafen.github.io/rbokeh/)

**G. Owen Zhang**

- speaker: [Owen Zhang](http://blog.kaggle.com/2015/06/22/profiling-top-kagglers-owen-zhang-currently-1-in-the-world/)
- "having good intuition is more helpful than being able to prove theorems"
- "it is counterproductive to talk about how you would be good @ something you haven't done before"
- it's very hard to change colleagues' initial perception of you
- discipline is important
	- proper validation framework during testing
- feature engineering is important:
	- read papers
	- look for universality classes (carry-over from other problems)

**H. Usama Fayyad: Data Security & Data Lakes**

- speaker: [Usama Fayyad](https://uk.linkedin.com/in/ufayyad)
- majority of enterprise data are unstructured
- "classic data" (internal) can explode when you pull in free contextual data (e.g. weather)
- any database can become "big" really fast
	- every company as "big data" company
- data takes turn from asset to liability quickly
- "Amazon sits on one of the world's most toxic data lakes"
- "nobody really uses MapReduce"
- cost of storage as big economic drive of Hadoop
- "computations comes to data"
- IoT --> detecting estrus in connected coews
- "once you have a platform, you can do a lot"
- Metadata
	- always forgotten
	- usually ignored despite criticality
- Radoop --> RapidMiner on Hadoop
	- "wisdom of crowd"

**I. Automatic Elbow Detection**

- [Sorites paradox](https://en.wikipedia.org/wiki/Sorites_paradox) --> "when does a heap of sand cease being a heap?"
- color as a discretization problem (in image recognition)
- data w/ "elbow" tough to use in raw form as model inputs:
	- need to "discretize"
- multicollinearity as a feature selection method
	- potentially best handled by PCA
- LASSO = "pretty cool"
- [Kolmogorov-Smirnov](https://en.wikipedia.org/wiki/Kolmogorov%E2%80%93Smirnov_test) test:
	- a nonparametric test of the equality of continuous, one-dimensional probability distributions that can be used to compare a sample to a reference probability distribution
	- "...quantifies a distance between the empirical distribution function of the sample and the cumulative distribution function of the reference distribution"
- [profile likelihood](https://www.stat.tamu.edu/~suhasini/teaching613/profile_likelihood.pdf)
- profile likelihood is not sclaable
	- long-ish computate time
	
**J. Julia pt 2**

- speaker: [Stefan Karpinski](http://karpinski.org/)
- profiler
- multiple dispatch:
	- Julia functions with multiple methods for various input types
- "unicode code entry"
- just-in-time (JIT) compiled

**K. Interactive Visualization in R**

- speaker: [Joe Cheng](https://github.com/jcheng5)
- ggplot2 as "gold standard of R visualization"
- [leaflet bridge for RStudio shiny](http://rstudio.github.io/leaflet/)
- [Leaflet](http://leafletjs.com/)
- [htmlwidgets](http://www.htmlwidgets.org/)
	- common foundation for invoking HTML/JS widgets from R
- [dygraphs for R](https://rstudio.github.io/dygraphs/)
	- interface to the JS [dygraphs](http://dygraphs.com/) library
- [ggplotly](https://github.com/tdhock/ggplotly)
	- takes arbitrary ggplot object and makes it interactive
- [RStudio Shiny](http://shiny.rstudio.com/)
	- "brokers conversations between R & JavaScript"
	- use interactive gestures to fetch data on the fly
- Hadley --> [ggvis](http://ggvis.rstudio.com/)

###DAY 2

**A. Deep Learning**

- "transfer learning"
	1. take a CNN already trained on other data
	2. push your own images through it
	3. pull out features from some layer
	4. use simple classifier on those features
- "build a similarity graph"
	- edges = images close to each other
- [Convolutional Neural Network (CNN)](https://en.wikipedia.org/wiki/Convolutional_neural_network)
	- "explicitly made for images"
- "use cosine similarity because they are sparse"
	- [cosine similarity](https://en.wikipedia.org/wiki/Cosine_similarity) = a measure of similarity between two vectors measuring the cosine of the angle between them
- Visual PageRank:
	- measure representativeness of images in their cluster
	
**B. Time Series Classification**

- speaker: [Mike Segala](https://www.linkedin.com/in/michael-segala-ph-d-5a65654b) of [SFL Scientific](http://sflscientific.com/)
- [Dynamic Time Warping (DTW)](http://www.psb.ugent.be/cbd/papers/gentxwarper/DTWalgorithm.htm)
	- time series alighment algorithm (originally designed for speech recognition w/ delays)
	- a modern distance metric
- traditional:
	- typical classification applied after removing temporal dynamics
- map "asynchronous parts together"
- DTW --> expensive grid search
- KEY: using K=1 + DTW leads to state-of-the-art performance across a variety of problems

###DAY 3