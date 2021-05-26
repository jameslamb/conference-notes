ODSC East 2021

https://live.odsc.com/


# Day 1

## A. The Tragedy of the Data Commons

* speaker: Prof. James A. Hendler,
* interoperability idea: if we focus on making data understandable to multiple systems, then we might share (as a data science community) the hard work of data cleaning
* "one way to solve the tragedy of the commons is for one person to buy the commons and charge everyone to put their cows in"

### B. Accelerate AI with Open Hybrid Cloud

* speaker: some guy from Red Hat
* this was a boring business talk

### C. How KPMG Data Scientists automate, accelerate, and enhance AI Workflows

* KPMG Ignite
* RedHat OpenShift - "the Kubernetes platform for open hybrid cloud"
* "you can do some random garbage in kubernetes"

### D. Dataset Management for Computer Vision: Possibly the Most Underrated and Important Component to Delivering Successful Computer Vision Models

* Author: Andrea La Rose, founder of remo.ai

### E. Deepnote - a Collaborative Data Science Notebook

* author: Itto Kornecki, Product manager at Deepnote
* "deepnote cretes visualizations really quickly, which means you're likely to use it"
    - in a cell where you print a data frame, a bunch of visualizations get generated in the background and you just click "visualizations" to see them in a tab
* supports SQL, R, Python
* DeepNote notebooks can be shared and you can collaborate in them interactively (just like Google Docs)
    * you can send a link directly to a notebook, and another person can jump into it
    * you can even generate links to individual cells
    * you can add comments on cells and tag people! Like in Google docs! what the fuck!
* you can also share a single cell and send it to someone
    - you could share the code or share the cell as a little bit of HTML
* if you run a cell like `!pip install <whatever>`, DeepNote won't let you. It will force you to update a `requirements.txt` file
* you can even get kicked to a text editor with a Dockefile
* you can click a little clock and say "schedule this notebook"
    - you can even sign up to get a PDF of the notebook emailed to you after each run

### F. Comprehending ClearML and MLOps

* author: Stef Telford (ClearML)
* really good presenter haha
* machine learning isn't really like other code
    - "compiling" a model isn't a deterministic process
    - does training count as part of "building"?
    - do you use a container or no? You probably need different dependencies for training than you need for scoring
* model tracking:
    - is the data cached?
    - does model scoring allow concurrency?
    - is any part of the scoring process stateful? can you reproduce that state?
* model reproducibility is really hard
* some components
    - ClearML server
    - ClearML Agent
* it kind of seems like ClearML is just capturing a bunch of other config information about models, and then allowing you to compare runtime, statistical performance, memory utilization, etc. of models based on those attributes
    - this is kind of how MLFlow works, IIRC
* https://github.com/allegroai/clearml

### G. The Data Science Challenge: How to Innovate, Upskill, and Inspire an Enterprise

* speaker: 3 schmoes from Liberty Mutual
* they have a "Data Science center of excellence" or some shit
* to get people a LibMutual involved in doing data science work, they ran an internal data science competition
    - to encourage best practices, they also refused to pay out prizes for teams that did not do reproducible work
* one data scientist gave his firsthand experience and said he learned a ton of stuff by being foreced to comply with the reproducibility rules

# Day 2

## A. Keynotes

they were trash

## B. The Next Evolution of PyTorch Performance Debugging

* speaker: Elena Neroslavskaya
* `pip install torch-tb-profiler`
    - a tensorboard-compliant profiler for pytorch
    - collect stack traces
    - alert when weights pass certain boundaries
    - can also be used with `torchscript` from C++
* pytorch.org/tutorials/recipes/recipes/profiler
* `nvidia-smi` doesn't actually give you details about stream-processing utilization on the GPU size
    - so you can't see how many of the SMs (streaming multiprocessors) are used by the kernels
* after this, the talk flipped to a pre-recorded demo that was very hard to hear
* pyorch.

## C. Automated Feature Engineering for Enterprise Machine Learning

* speaker: Ryohei Fujimaki, Lulu Liu (dotData)
* steps in feature enegineering
    - what data patterns are relevant?
    - how can we extract those patterns?
    - what patterns are statistically significant?
* lol of course, the magic is a `config/feature_engineering.json`
* in your configs you provide:
    - target
    - source
    - entity relationship (how do I join the data)
* given a config like that, they create a `feature_id` and the separately write a "feature explanation" (instead of trying to slam that information into a column name)
* programmatically generated different combinations like this allows you to broaden your view of possible features, and autoML is the thing that allows you to take this enormous space of possibilities and find meaningful stuff in it

## D. Enterprise ready ML Model Training on Hybrid Cloud, leveraging Kubernetes

* speaker: Saurya Das
* "install any OSS Kubernetes and isntall Arc agent"

## E. Going Beyond Matplotlib and Seaborn: A survey of Python Data Visualization Tools

* speaker: Stephanie Kirmer
* group bar labeling = nightmare zone
* `bokeh` "quad" = "making little boxes on the page"
* altair falls over if you use a dataset with more than 5000 rows
    - you'll literally get a "this is too much data" error
* `plotnine` is a Python port of `{ggplot2}`'s API into Python


## F. Introduction to Spark NLP

* speaker: Veysel Kocaman, PhD, Sr. Data Scientist | John Snow Labs
* SparkNLP makes NLP work in Spark
* github.com/JohnSnowLabs/spark-nlp-workshop

# Day 3

## A. Data Mastering at Scale

* speaker: Michael Stonebraker (MIT, Tamr)
* if you don't create silos, then all decisions have to go through "God", and business agaility goes out to the window
* independently created schemas are never just easily pluggable
* activities
    - get data into common units and meaning
    - line up columns that mean the same thing
    - deal with stuff like '-99 is actually NULL'
    - consolidate duplicates ("entity consolidation")
* gave the example of working with GSK...10 million+ columns
* in "traditional" schema integration, you draw lines in a GUI between pairs of matching attributes. But that's gonna be tough if you have 10 million attributes
* some rules-based systems
    - "if the edit distance between names is less than N, they are the same"
    - take the most frequent value when merging
* example of a system where someone wrote 200,000 rules for integrating schemas
    - no human can understand that many rules, so it takes forever to add new data sources
* data cleaning involves "ongoing stewardship". This is not a one-and-done process
* scaling up a pilot is not that easy
* Tamr does automated data mastering stuff

## B. Building a Robust Pipeline with the dag stack

* speaker: Sam Bail (Superconductive, the company that made Great Expectations)
* you can run a `dbt` pipeline as a task in an Airflow DAG
* great expectations: assertions for tabular data
    - create an "expectation suite"
    - you can use GE profiling to automatically "scaffold" expectations, to automatically create an expectation suite for something like "similar to this data"
    - Airflow has a built-in GreatExpectations operator
* github.com/spbail/dag-stack
* Astronomer is like containerized airflow
* to use `dbt`, you have to involve a relational database
* what's the difference between using `dbt` and the Airflow SQL operator?
    - `dbt` has some nice templating stuff that you otherwise have to do yourself

## C. Introduction to Deep Learning for Recommendation Systems

* speaker: Hagay Lupesko (Facebook)
* online recommendation system
    - improve business metrics through recommendations
    - log user and system activity
    - try to pick "10s of items" out of a much much larger catalogue, very quickly
* the baseline model for a recommendation is "popularity" (nothing personalized)
* "neural collaborative filtering"
    - embedding layer projects sparse inputs into dense vectors
    - dense user + item vectors are latent representations
    - these are fed into a "multilayer perceptron"
    - the output is the score (like a star rating)
* increase model complexity
    * embedding size
    * nmumber of layers
    * number of units in each layer
    * new interactions between features
* it's important that "drop out" only be active during training

## D. Tackling AI Bias

* speaker: Haniyeh Mahmoudian, PhD, Data Scientist | DataRobot
* to be clear, bias in machine learning means that models are working exactly as they're expected to
* identify "protected features" in your dataset
* maybe you want to ensure a fairness of outcomes, that is a statistical problem "based on these variables, no one part of the distribution of those values should have a different expected value than any other" or something (my notes, not sure she said this)
* there are correlated things that can still reveal, say, gender (even if you exclude a literal gender variable)
    - for example "if you have softball on your resume, you probably are a woman"
* how to mitigate bias
    - "just remove the protected attributes": it's not that simple, you could still have proxies
* mitigating bias
    - pre-processing: transform your data such that the target would not be correlated with protected attributes
    - in-processing: modifying the loss function in your algorithm to have fairness constraints
    - post-processing: changing the model predictions to avoid discrimination
* you have to decide your "margin of bias that is acceptable"
* thinking about the "cost vs. fairness tradeoff"

# terms

* Azure Arc for Kubernetes
* cognitive contract management (CCM)
* CUPTI
* deepnote
* embeddings in NLP
* fast.ai
* IBM Fairness
* lemmas in NLP
* libCUPTI
* libkineto
* Minio
* MLFlow
* MovieLens dataset (for recommendation)
* multilayer perceptron
* pytorch lightgning
* RDFS/OWL
* remo.ai
* "Semantic Web for the Working Ontologist"
* Seldon (something about MLOps / DevOps)
* Seldon-Core/Triton
* SparkNLP
* timbr.ai (KG/DB)
* URI-based name scheme (SRD, JSON-I)
* Volcano scheduler for batch, "gang" scheduling
