ODSC East 2022


# Day 1


## A. Overconfidence in Machine Learning: Do Our Models Know What They Don’t Know?

* speaker: Padhraic Smyth
* talked about the idea of model "confidence"
    - checking how well your model is calibrated for a classification task, you can check whether the model is "over-confident" or "under-confident"
* how to get better calibrated classifiers?
    - one thing that's common is to do "post-calibration"

## B. Accelerate AI/ML deployments with enterprise grade MLOps

* speakers:
    - Abhinav Joshi, some marketing schmo rom Red Hat
    - Matt Akins, solutions architect from NVIDIA
* first 10 minutes were just useless business jargon and clip art
* "with open source, you can easily monetize your components"
* the speaker from Red Hat had no idea what he was talking about
    - he was just saying random shit like "this has the key integrations and DevSecOps capabilities"
    - bro yo can't just smack a Jupyter logo up there under "ML/DL data pipeline" and be like "this is the architecture"
* the speaker from NVIDIA then switched to talking about the NVIDIA GPU k8s operator
* they wrote something called "automatic node labeling", which will go add k8s labels to nodes based on the types of GPU they have

## C. visiting the xpo hall

* https://iterative.ai/
    - data versioning company
    - founded by the creators of DVC
* https://www.metaplane.dev/
    - data lineage
    - slack alerts based on drift
    - has an email integration (so could work with VictorOps)
* https://aiven.io/postgresql
    - it's pronounced "ivan"
    - I asked what the benefit was over RDS, and one thing the guy mentioned was autoscaling
    - they have a terraform provider
    - postgres was their first offering

## D. Pandas workshop

* speaker: https://twitter.com/__mharrison__
* you can use `.astype()` with a dict!

```
df.astype({
    "some_col": "int8",
    "other_col": "int32"
})
```

* you can use `.memory_usage()` on a dataframe to get the memory usage of each column
* `inplace=True` doesn't actually often save memory
    - many of the implementations just create a new object and then swap pointers
* every column supports `.isin()` which tends to be faster than using `.apply(lambda x: x in ["a", "b"])`
* `.unstack()` shifts part of a multiindex up into columns
* summary:
    - `.apply()` is slow for math
    - don't mutate, embrace chaining
    - chaining operations will:
        - make code readable
        - remove bugs
        - easier to debug

## E. How to tell if something is graph-y

* speaker: someone from Neo4J
    - @CJLovesData1
* "if you have to do more than a couple SQL JOINs, then you might have a graph-y problem"
* tasks
    - classification
    - regression
    - clustering
    - dimensionality reduction
    - similarity
* did a kind-of-unfair comparison of SQL to Cipher where she even said "well I'm not that good at SQL"
    - but mentioned that an INNER JOIN is O(m x n) and the equivalent graph query is O(n)
* RDBMSs can be alright when
    - the queries are basic
    - there is no relationship between individual data points
* when you have more than a few joins, suspect that you might want to treat it as a graph problem
* solve graph-y problems with graph-y solutions
    - faster
    - easier to write
    - they are designed to take advantage of graph-y relationships
* someone asked "what's the best way to get data into this graph database"
    - and the Neo4j person said "we have a CSV uploader"

## F. Leveling Up Your Organization's Capacity for Data-Informed Decisions

* speaker: Mona Khalil (data science manager @ Greenhouse)
* good things:
    - well-defined and tracked metrics
    - cumulative documentation of insights
    - a formal program for evaluating and testing new ideas
* have an opinion about where findings go (and where they go to die)
* GreenHouse uses SageMaker Studio
    - how do I share a notebook? download it as a PDF?
* GreenHouse uses Mode Analytics
    - mentioned looking in there at reports that hadn't been run in years
* have an opinion about "questions you answer for curiosity's sake"
* are your insights accessible?
    - does everyone know the boundary between each tool?
        - do people know what goes where?
    - are your insights capable of being used and understood?
    - can knew and onboarding employees search for what they need to build domain knowledge?
* audit your tools!
    - you need a data discovery tool
    - GreenHouse likes Amundsen
* GreenHouse's stack
    - Amundsen
    - Mode
    - kyso
    - Hex
    - Tableau
    - SageMaker Studio
* Deliver the latest insights
    - they found that just sharing "hey here's some new stuff we did" helped the rest of the company understand what was going on
    - they do a "table of the month" (love that!) in the newsletter
* they do a twice-yearly "spring cleaning" sprint
* useful articles
    - "Five Principles of Self-Service Analytics (dbt)"
    - "Data Science Engineering Foundations (Shopfiy)"
    - "Don't Tell Your Data Team's ROI Story"

## G. From experimentation to product

* speaker: robert crowe (Google)
* there are attacks against models that can make them produce "catastrophic results"!
* level 0: manual process
    - a model registry
    - a prediction service
* level 1: ML pipeline automation
* TFX = "tensorflow extended"
* "TFX runs just about anywhere"
* TFX uses Apache Beam
* with TFX, you can even bring a non-Tensorflow model
* types of custom components:
    - python function w/ decorator and annotations
    - components using containers
* Waze uses TFX for large-scal data with low inference latency
* "Spotify was an early adopter of Kubeflow pipelines"

## H. Model-ready data with Snowplow

* "snowplow data platform enables any company to create and consume AI-ready data like Amazon, Netflix"
    - does that mean Amazon and Netflix use this? orrrrrrr
* Iglu = "deep schema technology"
* and there it is folks! First mention of "Modern Data Stack"
    - which apperntly includes plotly + SageMaker? chaos
* "snowplow is an open-source project but there's also a paid product"

## J. Wisdom of the Cloud

* speakers: Allen Downey + someone from DrivenData
* epistemic uncertainty
    - how much better could a model get?
    - how much better could could a model get?
* aleatoric uncertainty
    - how much better could a model reasonably get, given the information that is has?
* once the ensemble starts producing similar predictions to the best model, you might be at the aleatoric limit
* the score you get = `aleatoric_limit + epistemic_error`
    - where the "epistemic error" is random
* this is kind of a framework for deciding when to stop a competition
    - or, for a research team, when to stop working on a problem
* ensembling is "unreasonably effective"
* for ensembling multi-class classification probabilities, you could convert them all to logits, then average, then

# Day 2

## A. Keynote

* speaker: Hilary Mason, Hidden Door
* transformers = "learn from sequences but with a long-term memory"
* demo'd Hidden Door, which uses generative models to create a story similar to a D&D campaign
* art and the story are dynamically composed!
* "composable, understandable systems"
* hiddendoor.co
* so this is basically a site that generatively creates a story and little cartoons
* Hidden Door builds stories from composing previously-generated little templates together, to avoid offensive language

## B. Bridging the gap between data scientists and decision makers

* speaker: ken jee, Z by HP
* BLUF = "bottom line up front"
* described how the business tends to underestimate the effort required for data science projects, and IT tends to overestimate it
    - "the closest thing business people have seen to a data scientist is a management consultant"
    - "the closest thing IT people have seen to a data scientist is a software engineer"

## C. AutoML with PyCaret

* speaker: someone from Weights & Biases
* stack:
    - PyCaret for AutoML
    - Weights & Biases for experiment tracking
    - Prefect for running the stuff
* oh classic, he started by just importing a `train.csv`
* PyCaret has "a connection to pandas-profiling"
* W&B allows you to see a leader board between different models
* `nbdime` can be used to compare notebooks
* used Prefect Cloud + a Prefect Agent running in a Colab notebook :whoa:

## D. Distributed Python with Ray: Hands-on with the Ray Core APIs

* speaker: Stephanie Wang (engineer at Anyscale and lead committer for Ray)
* Ray was built at Berkeley
    - in the labs that built Apache Spark, Caffe, Apache Mesos
* architecture
    - a Ray "head node"
    - workers
    - each head node and worker runs a "raylet", which is a scheduler + object store
    - the head node also runs something called the "global control store"
* the `@ray.remote` decorator ensures that function calls return a Ray "object ref" instead of a raw object
    - and then passing those object reffs into things tells Ray to get values from an object store
* putting `@ray.remote` on a class makes it a Ray "actor"
* "doing large-scale data processing with Dask can be really slow"
* awesome talk!

## E. Containerization of ML

* two people from Cloudera
* "the dark times before containerization"
    - download data to laptop
    - run where the data is (e.g. in Spark)
        - but that leads to resource contention, dependency hell, security concerns
* some weird types of config files
    - `pip.conf`
    - `odbc.ini`
* challenges with "engines"
    - 1 engine version = 1 Python version, 1 R version
    - no support for arbitrary jupyter kernels
    - images must extend Cloudera base image (no other operating systems)
    - bloated docekr images due to installing everything in 1 image
* cloudera "ML Runtimes"
    - focused on Docker
    - runtime = 1 editor, 1 kernel, your choice of capabilities
    - add-ons become another dimensions mountined into the container (e.g. you tack on Spark or Hadoop)
    - you can mount in storage from something like a network file system
* "containerization is the right approach to support data scientists using shared infrastructure"
* Cloudera ended up at a place really similar to Domino
    - everything uses containers
    - you can think about Docker as much or as little as you want

## J. An Overview of AI for Cybersecurity

* speaker: Sagar Samtani, professor @ Indiana University
* made the case that that amount of data cybersecurity professionals have to work with is prohibitively large, and that that's leading to burnout
* cybersecurity datasets
    - VirusTotal
    - PhishTank
    - AZSecure HAP
    - Bot Repo, Twitter Bot-Cyborg
    - Credibility Coalition
    - Boss of the SOC, OmniSOC
    - NVD, Metasploit, ResearchSOC
    - KDD 1999
    - EMBER, NIPS Adversarial learning
* "DVSM score" for figuring out things with the most + most severe vulnerabilities

## To Google

* aleatoric uncertainty / episetimc uncertainty
* astropy
* Atscale
* Airbyte
* Amundsen
* DCGN
* DPU
* GraphFrames (Spark)
* gretel.ai
* Hex
* horovod
* Iglu (schema technology, from snowplow)
* kyso (knowledge repository)
* label smoothing
* link prediction (graph analysis)
* Metabase
* nbdime
* nipy
* Nmap/Zmap (in the context of "network-based fingerprint data")
* NVIDIA GPU operator for k8s
* RMSLE (evaluation metric)
* Stash
* sub-graph-level structural similarity (graph analysis)
* sunpy
* TFX
    - specifically using it without using Tensorflow
