# ODSC West
Santa Clara, CA

## Day 1

**A. Keynote: Sheamus McGovern**

- "being a data scientist is a tough gig"
	- it's hard to learn all you need to know to be a good data scientist
- it's hard to keep up w/ all the changing tools/techniques on your own

**B. Keynote: "How AI is Changing Data Science"

- speaker: Bob Rogers
- role: Chief Data Scientist
- firm: Intel
- the next stage after prescriptive analytics: "cognitive analytics"
	- develop systems to ask the right question based on context
- "the science of artifical intelligence is the science of data"
- the value of our skillsets to corporations is increasing
- Deep Learning:
	- field moving from feature engineering to toplogy engineering and network design
- autonomous vehicles need to:
	- recognize where they are on the road
	- recognize presence of objects
	- recognize *nature* of objects ("is that rectangle a building or a truck?")
- info:
	- GPS information
	- onboard video
	- communication w/ other vehicles
	- traffic control systems
	- audio from the driver
	- radar, LIDAR
- data collected at the edge, processed at the edge
	- but model training is done in the data center by data scientists
	- increasing importance of deployment concerns, reliability at the edge
	- how might you continuously monitor and improve your models with feedback from downstream?
- three reqs for data-driven AI future:
	- flexibility (need to be able to handle variations in which data streams are avaiable at any moment)
	- robustness (need to be able to gracefully handle variations in quality of our data streams)
	- continuity (need a process to monitor what's happening at the edge, pull in feedback, re-train, redeploy)
- AI can augment human capabilities
	- real time data
	- real time analytics
	- real time decisions
- *the science of aritifical intelligence is the science of data*

**C. Keynote: Software-Defined Servers: A Game Changer for Data Scientists**

- speaker: Gary Smerdon
- role: CEO
- firm: [TidalScale](https://www.tidalscale.com/)
- in-memory computing is key
- current approaches:
	- shard the data and spread across many servers
	- sample the data and hope it works
	- "all result in lower prediction accuracy"
- an example:
	- it's hard to discover relationships when you have to split the data into multiple servers
	- ideally, we want one big huge server to allow all data points to talk to each other
- high granularity:
	- decision trees model error rates decline with data size and tree depth
	- learning time decreases with tree depth
	- more data and greater tree depth consumes more RAM
- "software-defined server" idea from TidalScale
	- in-memory performance at scale
	- as many cores as needed
	- self optimizing
	- everything just works
	- use commodity hardware
- traditional virtualization:
	- run jobs on multiple virtual machines sharing a single physical server
- TidalScale pitch:
	- combine multiple physical servers into a single virtual machine
	- need to be able to run your software 100% bit-for-bit unmodified
	- you can keep adding compute services seamlessly
	- **software-defined servers are the future of servers**
- way faster to "move a process to the data" than to "move data near the process"
	- "use patented machine learning to transparently align resources"
- software side:
	- run any OS you're used to
	- run any apps you're used to
	- containers can scale across multiple physical servers
- TidalScale:
	- jobs scale linearly with data size
	- can bring more RAM to bear on problems to prevent R falling off "memory cliff"
- from IBM: "software-defined servers make it easy to run memory-intensive applications like data mining, machine learning, and simulation"
- Gordon Bell: "This is the way all servers will be built in the future"

**D. Keynote: Future of Data Science**

- speaker: Jermey Achin
- role: CEO + co-founder
- firm: DataRobot
- hopes and dreams:
	- drive adoption of open source in Fortune 500 and Global 2000
	- grow open source community: both users and contributors
	- increase quantity and quality of open source data science projects and technologies
- "I remember my life as a SAS programmer in an insurance company. I wouldn't wish that misery on anyone"
- R, Python, Spark don't talk to each other well
- hoped that ODSC would be a technology-agnostic conference:
	- rather than like PyData, R-specifc conferences
- another obstacle:
	- no open source roadmap
	- Scala, Python, XGBoost, R, Python, Java
- if you're a manager at a Fortune 500 company, you can't obviously sift through all the bullshit in open soure
- holding us back:
	1. dark lord Sauron (SAS)'s stranglehold over mission-critical stuff
- look forward to the machine-learning arms race
- roadmap:
	- 2019 - deep learning + neural nets ultimately disappoint and fall short of the hype
	- 2019 - more holistic research design, definition of "model" as full pipeline
	- 2020 - US + EU adopt law forcing you to explain machine learning decisions
	- 2021 - most DBs comply with "machine-learning readiness" (e.g. cell-level metadata, history, library of relationships)
	- 2021 - number of machine learning algos built and deployed in a single month exceeds global human populaiton
	- 2023 - machines can translate business problems in natural language nito properly formed data science problems
	- 2027 - some breakthrough in understanding of the human brain leads to a third neural net rush ("deeper learning")
		- this is where XGBoost, random forests finally go away
	- 2028 - Every Fortune 500 company has a computer on their Board of Directors that is tapped into all company data
	- 2031 - prior breakthroughs enable machines to automatically find problems to solve and things to optimize
	- 2033 - 70% of crimes predictable, regulators prevent law enforcement from utilizing these predictions
	- 2040 - the median value for where people predict the Singularity will happen
- dataRobot pitch:
	- meta-analysis of most likely model to work

**E. Competitive Learn Networks: Clustering with Self-Organizing Maps**

- problem: high-dimensional clustering
- self-organizing map = SOM
	- not practical currently
	- applicaiton: clustering wells based on microbial profile data
- k0- means = you provide the number of clusters
- SOMs will figure out how many clusters you have
- "similar colors end up next to each other spatially"
- more intuitive representation using "U-matrix Visualization Method"
- source code for this in Matlab
- "improved cluster identification and visualization using self-organizing maps"
	- Python and R implemented

**F. Applying Data Science to Connect the Unconnected**

- speaker: Avijit Mukherjee
- firm: facebook
- how can you use DS to facilitate infrastructure decisions?
	- example: detect where people actually live
- focus is on improving decisionmaking in designing connectivity infrastructure for remote rural areas
- 70% of people in rural areas do not have mobile coverage
- why don't we just deploy cell towers every 100 meters around the globe?
	- way too expensive
	- not consistent with where people actually live
- targeting where people live, what technology they have can help us intelligently prioritize where to build infrastructure
- one application: detecting settlements (*where do people live/work?*)
- output of the process is to divide a region into a 30m x 30m grid and detect whether there are houses there
	- then use clustering to find where houses are
- DBSCAN method
	- choose min number of neighbors
	- choose distance thresh
	- gives you classification as "core", "density-reachable", "outlier"
- DBSCAN params are adaptive to varying density across regions
	- nicely shifts for working on rural areas
- CURE - "hierarchical clustering using representative points"
	- finds points that are far from each other and far from the center
	- then kick off hierarchical clustering from there
- another clustering algo: "convex hull"
- w/ settlements identified, then you can go on to think about compactness, shape, proximity to other infrastructure like roads
-  country-specific choice of clustering method and parameter tuning necessary:
- advantages of two-phase clustering
	- computational
	- adaptive to local densities

**G. Machine Intelligence at Google Scale**

- speaker: Kaz Sato
- artificial neurons: basic behavior = classify data points into two groups
- gradient descent = adjusting the parameters gradually to reduce errors
- nonlinear example: need more than one neuron
	- a single neuron can only draw one line
	- each single neruon does simple linear classification...you tell it which spaces to separate
	- then combine results of the three neurons
- hidden layers:
	- these map inputs to a feature space, classifying with a "hyperplane"
- neural netowkrs allow you to avoid writing many if-else statements at the application level
	- just let the computer figure it out
- more hidden layers:
	- fit more complex surfaces
	- train on problems of arbitrary complexity
- [RankBrain](http://searchengineland.com/faq-all-about-the-new-google-rankbrain-algorithm-234440) = a deep neural network for search ranking
- [WaveNet](https://deepmind.com/blog/wavenet-generative-model-raw-audio/): generate human voice for any audio
	- can express any sound in any other sound's signature (think: in anyone's voice)
	- neural networks generating music never before heard
- Google Photos
	- Google will automatically tag your photos
- Inbox by Gmail
	- will look at the context of the email and recommend a response
	- around 10% of reponses on Inbox
- Google Translate w/ Neural Machine Translation
- Neural Net model for improving resource allocation in a data ceneter
	- improved power usage effectivieness (PUE) by 15%
- Google is now using deep learning for 60+ projects
	- Android
	- Apps
	- Gmail
	- Maps
	- Photos
- big takeaway: deep learning is a stable technology, production-ready
- [cloud vision API](https://cloud.google.com/vision/):
	- image analysis with pre-trained models
	- REST API: receives an image and returns a JSON
	- generally available
	- can be used to detect emotion on facial expressions
- [cloud speech API](https://www.google.com/intl/en/chrome/demos/speech.html)
	- pre-trained models
	- REST API: receives audio, gives back JSON
	- demo: https://www.google.com/intl/en/chrome/demos/speech.html
- [cloud natural alanguage api](https://cloud.google.com/natural-language/)
- a bunch more stuff at https://cloud.google.com/products/
- [TensorFlow](https://www.tensorflow.org/): an open source library for deep learning
- it's really hard and expensive to build and maintain GPU cluster
- TensorFlow for windows is coming soon
	- TensorFLow can call predict on the cloud or mobile/IoT devices (you don't need your own prediction server)
	- portable across OS (e.g. trainin on Mac/Windows, predict on Android, iOS, RasPi)
	- offers distributed training
- democratization of deep Learning
	- look at [TensorFlow powered Cucumber Sorter](https://cloud.google.com/blog/big-data/2016/08/how-a-japanese-cucumber-farmer-is-using-deep-learning-and-tensorflow)
	- outsource tedious stuff to computers, give people time to do what they love
- [Borg](http://blog.kubernetes.io/2015/04/borg-predecessor-to-kubernetes.html)
	- no VMs, purecontainers
	- 10K-20K nodes per cell
	- CPUs, mem, disks and IO
- distributed systems for large neural network
	- CPU/GPU scheduling
	- communications
		- local, RPC, RDMA
		- bit quantization
	- cost-based optimization
	- fault tolerance
	- more nodes = higher probability of at least one failure
- [Google Cloud Machine Learning](cloud.google.com/ml)

**H. Stacking Models**

- Win-Vector is a small consulting company doing data science
- [slide repos](github.com/WinVector/NestedModelsTalk)
- they wrote "Practical Data Science w/ R"
- "if you're working with R and not making pretty graphs there's something wrong with you"
- a lot of significance testing is done against "nothing"
	- "it's often easy to do better than random"
	- you are presenting a "challenger model"...not the first one
- most classification models return probabilities or at least are naturally geared that way
- p-value on AUC is "probability that a null model (useless model) could achieve perforamnce at least this good by chance"
- R package --> sigr
	- formats results close to American Psychological Association standards
- you cannot pass a frequentist significance test
- deviance = "expected log-embarassment"
	- penalizes claiming events that happened were rare
	- good double check of model calibration before going into production
	- catches "did your prediction do something identifiably ridiculous?"
- business people just want "accuracy"
	- they mean this in colloquial terms
	- they pretty much never mean accuracy
- AUC + deviance let you worry about what to do with your qualifier
- Z and p
	- p is uniformly distirbuted in the interval [0,1]. If you have no effect, you don't get a p of 1
	- Z is roughly normally distributed with standard deviation 1
- if there is an effect:
	- Z goes to infinity as n increases
	- p goes to zero as n increases
- Z, p give you only existence of effect, not size
- effect size: Cohen's d
	- d is the effect size divided by the standard deviation of individuals (not the population mean as with z)
	- d = z/sqrt(N)
	- d = 0.2 is small, d = 0.5 is medium, d = 0.8 is large
- testing packages:
	- [pwr](https://cran.r-project.org/web/packages/pwr/pwr.pdf)
	- [boot](https://cran.r-project.org/web/packages/boot/boot.pdf)
	- [sigr](https://github.com/WinVector/sigr)
	- [cvAUC](https://cran.r-project.org/web/packages/cvAUC/cvAUC.pdf)
	- [WVPlots](https://github.com/WinVector/WVPlots)
	- [vtreat](https://cran.r-project.org/web/packages/vtreat/vtreat.pdf)
- "if two models are nearly indistinguishable, it would take infinite data to define which is better and your business wouldn't be any better off"
- nested models
	- first, train a bunch of base learners
	- then, train some meta-model to ocmbine their predictions
- ensembles, stacked models can improve prediction performance over performance of single models
	- intelligently combine models w/ different learning biases
- ensemble learning
	- boosting (1996)
	- bagging (1996)
	- random forest (1995)
	- several diverse (usually) low-complexity learners that vote on outcome
	- different algos = different ways of getting diversity
- stacking:
	- stack up some more complicated base learners
	- extension of hyper-param tuning
	- strong learners, higher-complexity meta-model
	- "can I jsut keep all my models?"
- another form: "mixture of experts"
	- take high-complexity base learners
	- change weights for combination by a gating function
	- often neural net based
	- trying to "re-infer the areas of expertise"
- any pre-model fitting task that uses knowledge of outcome is a nested model
	- variable treatment
	- hyperparameter tuning
	- scaling of the varibales
	- Y-aware dimension reduction
- see [H2OEnsemble](https://github.com/h2oai/h2o-3/tree/master/h2o-r/ensemble)
	- also [SuperLearner](https://cran.r-project.org/web/packages/SuperLearner/SuperLearner.pdf)
- perils in choosing meta-model
	- "complexity" of a model is like "ability to explain rich patterns in data"
	- high complexity models basically start trying to explain unexplainable variation in predictions from base learners
	- low-complxity meta-models have bounded excess generalization error ("not as able to overfit")
	- linear regression and logistic regression are decent low-complexity choices...but the inputs are correlated!
	- **best regression choice (per Breiman):** use least squares confained to have non-negative coefs. Or ridge regression
- issues w/ high-cardinality categorical variables:
	- under the hood, models are actually treating a k-level categorical var as k-1 indicator vars
- alternative: effects/impact coding:
	- re-encode the categorical variables as a few numerical variables
	- but think about this...the impact code actually is a "base learner"
- complexity related to "ability to memorize training data"
- don't use the same model to train your base models as you do to train your meta-models
	- this bias comes through only with high-complexity learners
- to do:
	- training set to build the learners
	- calibration set to build the meta-model
- statistically inefficient = "getting as good a model as is possible given the maount of data you have"
- **If you have a very very very rare target variable, you don't have big data**
	- effective size of a dataset is twice the number of positives
- idea 2: simulate training models on different data than you train your meta-model on
- summary:
	- training data reuse increases nested model bias
	- high-complexity models (base or meta) increase nested model bias
	- use (simulated) out-of-sample data for meta-model training
	- prefer lower-complexity models when feasible
- workflow:
	- use training data to train base models
	- create simulated out-of-sample base model features
		- calibration set, cross-frame, Laplacian noise
- strong recommendation: Leo Breiman's paper on Stacked Regressions

**I. Pipelining in R and Python plus Docker**

- speaker: Dr. Ali Marami
- firm: R-Brain
- R-to-Python in memoery:
	- %R magic and %Rpush
- through  disk
	- CSV files
	- [feather](https://blog.rstudio.org/2016/03/29/feather/) (easy to use, fast, much better than CSV files but yet to be optimized for very large files)
		- "Hadley and Wes just sat together and did this"
	- [parquet](https://parquet.apache.org/) - not easy to use but optimized in size and relatively fast
		- columnar datastore
- using ```feather``` in R
	- ```library(feather); read_feather(path)```
- using Parquette is a bit more complicated
	- you have to install Spark
	- you need to define wherever your Spark stuff is located

**J. AnalyticOps and Analytic Engines**

- speaker: Stu Bailey
- firm: Open Dta Group
- lots of focus in reasearch on finding/designing better analytics
	- but this doesn't move much the actual value to the organizaiton
	- but if you can't get it into produciton, does it really matter?
- you need to start measuring deployment metrics
- ODG experience:
	- most companies don't have people institutionalized analytic ops
	- you usually find a few people w/ good people skills who just make the deployment happen
	- "Anaytics Ops"
- four challengins in analytics deployment:
	- IT needs to manually recode models
	- compmlex models are hard to deploy
	- model scoring too slow
	- too many languages to support
- common situation:
	- write something in R/Python/MatLab, then hand off to Engineers to recode in Java
	- "you are not stuffing your R code in my app...I'll get fired if it breaks"
- a "score" in ODG case is "outcome of an analytic on data you've never seen before"
- **"Data science appears to be to computer science what computer science is to electrical engineering"**
	- things changing really fast
- relational DBs didn't come onto the scene until 1971
	- a lot of code had been written before then
	- database is "such a useful abstraction that we don't even think about it"
	- merger of analytics and business code could be a similarly useful abstraction
- devOps = "building production software stacks"
- data scientists need to drive the decision about which tools can be used
	- don't build a suboptimal tool because it's hard to get into production
- aspiring analytic designers...working in the deployment area is a great place to start
- A "model"
	- input that is well-typed (AVRO schema)
	- output that is well-typed (AVRO schema)
	- intialization - run once
	- action - the math
- a stream:
	- scema = an AVRO schema
	- format = JSON, AVRO binary, text
	- identifier = Kafka Topic (pub/sub), file name, port
- "we tend to like Docker as a platform for deploying analytics"
- new deployable conception of "model" as a very useful abstraction
- **Automate and Scale**
	- docker ecosystem schedulers (Mesos)
	- Data Bus (Kafka)
	- Think about a fleet of analytic engines chaining the outputs together at the infrastructure level
	- Linux containers (Docker)
	- run a bunch of containers --> Mesos, Kubernetes
- handoff in the ODF workflow means that data scientists don't have to be involved in all the details of implementation
- main constituencies:
	- devops can wire in an analytic without knowing it ahead of time
	- data science - develop analytics and get them into the business faster
- **"We think languages like PFA and PMML are very useful IN SOME USE CASES"**
	- should not put a burden on the data designer in terms of what language they use to articulate the math

## Day 2

**A. Working with Graph Data**

- firm : neo4j
- for all the info see [Neo4j website](https://neo4j.com/download-thanks/?edition=community&release=3.0.6&flavour=osx&_ga=1.27854908.1483889934.1478452426)
- example use case: Netflix is giving you graph-based recommendations
- graph DBs are "white-board friendly"
	- the data representation feels like the actual data
	- graph data feels natural
- Noe4j is transactional (different from other noSQL things)
	- can be schema free but doesn't have to be
- Cypher = "a pattern-matching query language made for graphs"
- users the query language [Cypher](https://neo4j.com/docs/cypher-refcard/current/)
- ```MATCH (:Person {name:"Dan"}) -[:LOVES]-> (whom) RETURN whom
- setting up schema example:
	- ```CREATE CONSTRAINT ON (p:Person) ASSERT p.name IS UNIQUE```
- one graph = one DB
- you cannot do joins on two graphs
- you can store any java primitive as an attribute in the DB
- "index-free adjacency"
	- no index used to look up all the nodes a node is connected to
	- local traversal will have the same performance regardless of graph size...as long as you start from a well-defined starting point
	- in contrast: a JOIN in something relational is based on an overlap of two sets (perforamnce breaks down w/ bigger datasets)
- so how do you find well-defined starting points?
	- you should be searching based on indexed properties
	- ```CREATE INDEX ON :Person(name)```
	- note that when you create a uniqueness constraint, you get the index along with that
- there is a built-in query profiler!!!
	- just append ```PROFILE``` to the beginning of your Cypher query
	- every Cypher statement is translated into some lower-level database operations

**B. Undeniable: How to Build a Narrative for Disruptive Innovation**

- speaker: Michael Margolis
- role: CEO
- firm: Get Storied
- see [their website](https://www.getstoried.com/)
- consider three examples:
	- plain zippo lighter
	- zippo lighter from WW2
	- zippo light w/ a WW2 general's inscription on it
- why are these different value? the story!
- Ben Horowitz: "A company without a story is usually a company without a strategy"
- when we're in a story, we've agreed to suspend disbelief
	- but not true in business. In business you face disbelief, skepticism
- "how do you take a world-changing idea and share it so it doesn't get lost in translation?"
- **dead is dead**
	- people need context
	- people need emotional content
- Google example:
	- 5% of in-store purchases in 2011 were influenced by digital channels
	- 70% today
- what is your "out of sight"?
	- people need to see it and feel it before they can believe it?
- **definition**: Stories are...
	1. made of facts 
	2. that are wrapped in emotions 
	3. that compel an action 
	4. that changes the world
- find this --> what is changing in your world, your industry?
	- use that change to legitimize the story you want to tell
	- when you use change, it helps people to understand why there is a story to be told
	- then give evidence on how what you're proposing can help meet the new reality
- "there are few superheroes who are born superheroes"
	- instead they become heroes based on circumstances they're in and the choices they make in those circumstances
	- we all have a backstory, something about origin, that gives insights into how we see the world and what makes us tick
- the exploratorium:
	- "there are no rules on what or how to create"
- provenance: "the more history something has, the more valuable we perceive it to be"
	- the value is in the story	
- see their [online courses](http://www.getstoried.com/redpill/) on telling your stories
	- "if you take the red pill, you'll never see the world the same again"
- dealing with "show me the data" when you haven't had the system to connect it yet
	- telling the story w/ the right context and enough emotional content, people will want to go on that journey with you
	- context, emotion, evidence
- TAKEAWAY: **The story matters**.
- think about AI...biggest challenge is teaching the machine context
- **IDEA:** share the exercise below w/ Gentzy? As a potential all-hands exercise

An Exercise:

- pair up, each person shares 30s on these 4 questions

Q's

1. Where were you born and raised? How has it shaped how you see the world?
2. Who are your parents? How are you like them? How are you different?
3. What are you curious about? What are you trying to learn?
4. What is it about where you come from that helps explain why you do the work that you do?s

- w/ the same partner, do a one-directional, one-person share. Describe:
	- where did the person light up?
	- what is their passion?


**C.Data-Driven Decisions for Long-term Product Success**

- speaker: Ahmad Anvari
- firm: Facebook
- 1 billion messages on messenger
- 60B+ Messenger + WhatsApp
	- 3x bigger than total SMS traffic
- business can communicate on Messenger as well
	- you can send messages to the owner of an FB page
- 1. define a "north star" metric:
	- the thing that guides everything else
- 2. Measure and track
	- "if you can't measure it, you can't improve it" - Lord Kelvin
	- the defiontion of what needs to be optimized should not change
	- you should log every user interaction as a potential data source
	- anomaly detection is very important...see "$200 Best Buy gift cards for $15" issue
- you have to do random experiments to fight against biased samples

**D. Natural Language Processing w/ Graphs + NLP**

- speaker: William Lyon
- firm: neo4j
- very complex data becomes difficult to model in relational DBs
	- lots of joins
- "index-free adjacency" in graph DBs
	- every node has a pointer to every other node it is connected to
- nodes are the entities in the graph, relationships connect them
	- nodes can be labeled
- Cypher: a graph query language
- we traverse the graph from some well-defined starting point
	- we use an indexed lookup to find the node to start from







