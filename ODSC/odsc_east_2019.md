# ODSC East

May 2-3, 2019
Boston, MA

## Day 1

**A. Keynote: Maureen Mcelany**

- "Building Trust and Transparency into the ML Lifecycle"
- developer advocate at IBM
- Northpointe's COMPAS algorithm
    + Northpoine has changed its name
- "Data for Black Lives"
- check out Anil Dash on Ezra Klein's blog
- "the majority of these popular machine learning algorithms are being written by cis white men"
- Pinterest was one of the first large tech companies to publish information on the diversity of its workforce and progress on it's internal D&I efforts
- "AI Fairness Toolkit" open source project from IBM
    * https://github.com/IBM/AIF360
    * https://aif360.mybluemix.net/
- IBM Center for Open-Source Data and AI Technologies
- IBM has an internal certification process where it teaches people how to contribute to open source projects
- http://ibm.biz/codait-projects

**B. Keynote: Hilary Mason**

- "The future of AI and ML products"
- "When she was 4 years old, she told her mother she wanted to be an astronaut, a computer scientist, and a cab driver when she grew up. And she still wants to be two of those things"
- let's make AI boring --> let's make it useful
- "I love Google Maps traffic view because it's SO BORING"
    + but it's a super powerful tool
- there's a dead, British character actress named "Hilary Mason"
    + in 2009, a startup called Cuil sprang up to mix text and photos and mixed the actress and her up
- Named Entity Recognition is super hard
- the other Hilary Mason was in this movie called "Robot Jox" about robots punching other robots
    + this is so important, omg I love this talk
- "executives love pyramids"
- SUCH a good progression:
    + "big data": you could put all your data in one place and count it
    + "analytics": you could count things for a business purpose
    + "data science": you could count things cleverly
    + "machine learning": you could count things REALLY cleverly with some feedback mechanism
    + "AI": you could count things with complicated feedback mechanisms
- "the little-known story of the first IoT device"
- the opportunities for doing impactful work at large companies is underappreciated
    + "to do data science you need data. Startups don't have that"
- "the data you analyze leaves scars"
- "Fast Forward Labs" blog: https://blog.fastforwardlabs.com/
- applying ML in 2019
    + you need a vision and prioritization framework
    + think about projects as investments and how they enable others
    + "invest in a portfolio of capabilities"
- I can't tell you how often I see people build a cool model and then hand it off to data engineers to "make it fast"

**C. "Elementary Data Science"**

- speaker: Josh Wills
- I worked on rebuilding Slack Search, now I work on tooling and systems infrastructure
    + how they run experiments
- "does anyone not know what Slack is? any Google employees here?"
    + "Slack is Kafka for people"
- "your ML test score": https://ai.google/research/pubs/pub45742
- when you start learning about unit testing code, you just think "well I'll do this because smart people said I should"
    + but eventually you get to the point where thinking about testing makes you actually write better code
    + thinking about monitoring is the same! you have to think about how things can fail
- "this is my mid-life crisis in talk form, for your benefit"
- "data science is advanced counting, with some occasional division"
- mentioned an article by Charles Munger
- what's been successful about data-driven companies is the ability to apply principles of data science at every level of the organization
    + the ability to think quantitatively and invert problems is so powerful
- another mention of the "where to put armor on WW2 planes" example
- think about measuring the effectiveness of a model to figure out what snippets to show with search results
    + super hard problem
    + if the snippets are really good, people might get what they need from it and not click!
    + if the snippets are bad, people might click more
    + Google decided to measure the impact of this differently. Instead of "try to drive more positive behavior", they thought about "reducing negative behavior"
        * [he didn't give details, so I'm guessing]: the metrics they came up with were like driving down the rate of people who end up clicking into a result, then coming back out and clicking into a different results
- "41 shades of blue" experiment
    + a few years ago, a team of like 25 people ran experiments on the Google Ads interface
    + the Ads UI team did one launch that made Google like $600million in incremental revenue
- [Hanlon's razor](https://en.wikipedia.org/wiki/Hanlon%27s_razor): "never attribute to malice, that which could be attributed to stupidity"
- don't confuse the map for the territory
    * https://en.wikipedia.org/wiki/Map%E2%80%93territory_relation
- Seven Powers: how to create competitive advantage
    + https://www.amazon.com/7-Powers-Foundations-Business-Strategy/dp/0998116319
- "I don't really watch Gracie & Frankie, but heard it's good. Do people like it?"
- "whenever you heard about an internal conflict being leaked, it's always the loser leaking"
- "Astroball: the new way to win it all"
    + https://www.amazon.com/Astroball-New-Way-Win-All/dp/0525576649
    + The Astros had to make a really hard, subjective decision about trading for Justin Verlander and they were "honest about it" and didn't "try to dress it up with data"
    + J.D. Martinez spent a summer jst working on his swing and came into camp and told the Astros "hey my mechanics are better now, let me show you what I can do". They had models that said basically "hitters don't get better in their 30s". They traded him to the Tigers...and he won the MVP and hit .400 in June
- Google built a culture of experimentation
- Josh: I personally don't make a lot of data-driven decisions in my personal life.
    + "I think I'm still in the midst of my mid-life crisis"

**C. Achieving Salesforce-Scale Machine Learning in Production**

- speaker: Sarah Aerni. Director of Data Science, Einstein Platform
- flavors of ML in prod
    + "models that inform strategic decisions" (data-driven drug discovery)
    + "models that are products" (chatbots, algorithmic trading)
    + "models that augment products" (predictive lead scoring)
- it can be non-trivial to hire data scientists!
    + the number she's using is average salaries around like $80,000
- how they "democratize data science and AI":
    + out of the box AI for Business Users
    + point-click solutions for admins
    + APIs for developers
- why you need to have a platform: 
    + hiring another data scientist every time you want to build a new app doesn't scale
- "fix your leaks":
    + frequently, customers want to build models
    + they SAY they know exactly what they want to build and model
- "Make sure everything is as simple as it can be, but no simpler"
- why you need a platform:
    + monitoring to inspect and alert on models
    + application to deliver predictions to customers
    + pipelines to deliver data to scoring
- data scientists frequently either don't think about all of these productionalization concerns or they only think about them in the narrow space of a single application
- TransmogrifAI
    + an open-source autoML library for structured data
    + the main goal was code re-use
- AutoML isn't going to replace data scientists! It just makes them more productive and let's them try more ideas
    + think of AutoML as a "tournament of models"
- you HAVE to design in metrics early
    + total number of predictions per hour
    + total predictions per week
    + distributions of predicted scores
    + model performance (statistical)
- she explained how Agile methodology works for app dev and then made that translation for DS
    - lesson 1: figure out with the business what "good enough" looks like
        + iterations (new features, more data, better data) can come later. But the only way you'll know you need to do that is feedback from monitoring
- this was a REALLY good talk on how to use principles from software engineering to inform model building (and how having a platform enables that)
- "I promise, I know that "
- Never deploy a model without a plan for iteration:
    + how can your data scientist experiment?
    + how can your data scientists redeploy?
    + what will you do with your old predictions?
- github.com/salesforce/TransmogrifAI

**D. Scalaing AI Applications with Ray**

- Richard Liaw
- Ray is a high-performance distributed computing things for training models
- Ray has been used at:
    + Alibaba
    + Intel
    + Microsoft
    + facebook
    + Ant Financial
    + Ericsson
- motivation
    + Spark runs in a synchronous, bulk pattern
    + results in low utilization of the cluster since workload runtime is determined by stragglers
- the Ray API:
    + functions are converted into "tasks"
    + you can use this `@ray.remote` decorator to say "run this function somewhere else"
    + you build up a workflow that creates futures, and then use `ray.get()` to say "ok start executing"
- Q: "what happens if one of the function calls results in an exception"
    + A: "it won't destroy your whole cluster"
- architecture
    + there is a driver process on where you invoke your script, and then multiple worker processes running on other nodes
    + Ray supports nested parallelism
    + every node will run an object store (`plasma`) for use by the workders
- tutorials: https://github.com/ray-project/tutorial
- there were a bunch of New York Fed people in front of us at the talk who said they use Ray
- `tune`: distributed hyperparameter search in Ray
    + https://github.com/ray-project/ray/tree/master/python/ray/tune
- `tune` is aware of your hardware layout and knows how to do both of these:
    + have one GPU share multiple models
    + have one model benefit from multiple GPUs
- you can chagne from a single machine to a large cluster with 0 code changes
- `tune` is compatible with Keras, Tensorflow, Torch, scikit-learn
- "architecture search" is honestly really similar to hyperparameter search
- RLlib
    + "a scalable and unified library for reinforcement learning"
    + RLlib is now officially a part of Sagemaker

**D. Neuroevaluation-based Automated Model Building: How to Create Better Models**

- speaker: Keith Moore, Director of Product Management, SparkCognition
- guy started with weak small-talk about weather
- history
    - the core application we focus on is predictive maintenance
    - our first engagements were with some huge utilities
    - one of their customers talked about SparkCognition at a conference and got them a bunch of leads
- things they try for
    + "democratize" (maximize scale of data science teams by democratizing model building)
    + "automate" (automate model-building)
    + "self maintain" (quickly adapt to changing conditions over time with automated model retraining)
- "we built a platform with the explicit purpose of making our internal data scientists more productive"
- "feature engineering is just math"
- he equates neural architecture search to hyperparameter optimization
- architecture search is hard -> it's a super difficult combinatorial problem
- Biology-inspired autoML: Lamarck vs. Darwin
    + https://www.quora.com/What-are-the-major-differences-between-Darwin-and-Lamarcks-theories
- backpropagation is "a Lamarckian way of teaching NNs how to fit to data"
- NEAT:
    + https://en.wikipedia.org/wiki/Neuroevolution_of_augmenting_topologies
    + https://github.com/CodeReclaimers/neat-python
- when we started building Darwin, we thought we could build a platform with all these architecture search approaches and make it usable for all data scientists
- Darwin has the concept of "grammars" which means basically "collections of architectures that are meaningful given some characteristics of the input data"
    + the example given was "you wouldn't use LSTMs if you don't have timeseries data"
- Question in the room: "how do you select the hyperparameters that are introduced by the genetic algorithm itself?"
    + "those are also dynamic and are modified from generation to generation"
- Normal Behavior Analysis:
    - "using autoencoders and sliding windows to detect changing behaviors over time (e.g. degradation)"
- Darwin is being used by dozens of customers globally
- some customers will use Darwin just for scaling models. So a data scientist will build the first model in Darwin, and then someone else will use Darwin's model deployment stuff to scale it to many sites / assets
- Darwin has some custom "getting feature importance from neural networks" stuff
    + oh or maybe not? After he said that he namedropped LIME and SHAPley values

## Day 2

**A. Keynote: Clive Thompson**

- before the News Feed, Facebook was super slow to use
- the Facebook news feed algo favors aggressiv eposts or conspiracies
- "in the early U.S., the people who wrote the code were lawyers"
    + they made design decisions with impacts they couldn't see
- civil engineers and architects similarly had to make impactful design decisions 100ish years ago
    + e.g. Robert Moses
- The first `Hello world` example was written in a tutorial for the language `B`
- if there is any place that needs more automation right now, it's the government
- "software is sitll one of the most powerful fulcrums for human potential"

**B. AI and Security**

- now you can use AI to do social engineering attacks with "deep fakes"
    + fake voices, fake video
- it's common to just add security later:
    + "celebrate the accomplishments THEN explain the risks"
- the worst problem is "purposeful, malevolent design of AI systems"
    + there is very very little research on malevolent use of AI
    + very many problems being described and very few solutions
- democratization of AI also means democratization of the ability to use AI maliciously!
- children are untrained neural networks deployed on real data

**C. The role of Big Data Analytics in Industry 4.0**

- Alex Lazarevic, Black and decker
- "six blind men and elephant" story
    + https://en.wikipedia.org/wiki/Blind_men_and_an_elephant
- "limited experiences often bring partial or innacurate view"
- "creation of new products leveraging sensors and data to deliver measurably better or new outcomes"
- examples cited:
    + Rolls-Royce has started selling data on its engines to airlines so they can track faults and failures
    + Philips invented a toothbrush with sensors that will tell you where you need to brush more
- companies expect to increase annual revenues by average 2.9% with total expected annual increase of almost half a trillion dollars over the next 5 years
- things that prevent projects
    + resistance: mfg is conservative
    + old equipment can't always easily be retrofitted to collect data
    + lack of analytics knowledge in leadership and workforce
    + lack of partnership among many players
- "machine learning for early fault detection"
    + very few labels (faults are rare)
    + heterogeneous data
    + dynamic / temporal nature of data
    + techniques we use:
        * tree-based supervised learning
        * anomaly / change detection with neural nets
- anomaly detection approaches:
    + nearest-neighbor
    + density-based
- CUSUM persistence change detection method
    + CUSUM is a sequential analysis technique typically used for monitoring and change detection
    + "high-side" CUSUM on Anomaly Detection scores to detect only changes in the positive direction
- how they do anomaly detection
    + get an anomaly score
    + do change detection on top of it (with e.g. CUSUM)
- Q: "did you find that some types of failures are easier to predict than others?"
    + A: yes. Whenever you are applying anomaly detection, you will "not get what you hoped for". It will give you abnormal situations but no further details

**D. AIOps: Anomaly detection with Prometheus**

- speaker: Marcel Hild, RedHat
- "I'm working at a small startup called RedHat" :joy:
- Project Thoth
    + http://thoth-station.ninja/
- OpenDataHub
    + http//bit.ly/2y6Nh6m
- Prometheus explained:
    + targets = "the things you are monitoring"
    + targets expose metrics endpoints and prometheus then polls those (over HTTP)
    + Prometheus then adds a system time to those metrics
    + you query the attached db with PromQL
- it's often preferred to use influxdb for your data scientists
    + reliable historical data storage
    + easily hooked into prometheus with write and read endpoint
    + BUT....the distributed version of influxdb is closed-source (:sad-face:)
    + also this thing eats RAM for breakfast
- so they went with a different approach...
    + scrape prometheus with an HTTP scraper
    + container can be configured to scrape any prometheus server
    + stores data in ceph or S3 compliant storage
    + bit.ly/qQw9pho
    + and then use spark: http://bit.ly/2PIZZVG
- Thanos
- they talked about using TSNE for spotting anomalies in metrics data
- they use prophet for forecasting metrics
- github.com/AICoE/prometheus-anomaly-detector
- "we think comparing multiple timeseries is too hard"
    + we tried a library that allows you to pick up anomalous deviations from historical correlation, but it only works for pairs of timeseries
    + "you would need a subject matter expert to be able to solve that problem of detecting anomalous correlations between on the order of hundreds of timeseries"

**F. From Zero to Airflow: Bootstrapping into a Best-in-Class Risk Analytics Platform**

- speaker: from BlueVine
- github.com/ido-sh/odsc_presentations
- another one of those talks about like "we started with a swamp of cron jobs"
- made the good point that crons have hidden dependencies
- the first thing you should do in the transition is take those crons and schedule them as "singleton" airflow jobs
    + that means you aren't taking advantage of the DAG structure of the processing, but at least you're all in Airflow land
    + then you can prioritize which things to start breaking up
- bad things:
    + no user-specific access roles
    + scheduler can silently die
        * if your monitoring also runs on Airflow, then you'll never get an alert that says "Airflow is down"
        * you have to do monitoring external to Airflow
    + tasks can become zombies
    + scheduler performance quickly becomes a major bottleneck
        * they were surprised, thought the type of workers would be the main thing that defines performance
- problem: bloated airflow DB
    + big DB -> slower queries -> slower scheduling
    + DB contains metadata for all dag / task runs
    + high dag frequency + many dags + many tasks
    + under our setup, the DB had like 4 billion cals and grew over 15 GB
    + solution: run a weekly archive of data older than 1 week
- problem: inefficient querying mechanism
    + solution: github.com/apache/airflow/pull/4751
- problem: Airflow scheduler cannot prioritize its own resources
    + scheduler has to continually parse all DAGs
    + not all DAGs are equally important
    + but all get the same scheduling resources
    + solution: put time-sensitive stuff in a second one
        * dedicated instance = less dags / tasks = faster scheduling
- how you get your dag deployed:
    + make a pull request to a repo run by data engineers 

**G. ETL with no page duty**

- CarGurus
- this is another "how we use Airflow"
- WOW they used the Brad Pitt DAG meme
- their stack:
    + Github --> Jenkins CI --> Airflow --> container orchestration
- you can use alerts "to build trust"
- it's important to build in self-service debugging for people early so they can help themselves
- check out the CarGurus Engineering blog: https://blog.cargurus.com/

## New terms

* ceph
* CUSUM
* Larmarkcian vs. Darwinian Evolution
* BuildKite
* Prometheus
* Pachyderm
* [Thanos](https://blog.openshift.com/thanos-long-term-storage-for-your-prometheus-metrics-on-openshift/)
