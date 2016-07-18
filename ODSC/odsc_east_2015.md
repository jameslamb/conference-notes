# Open Data Science East (2015)

## Conference Details

Location: Boston, MA
Dates: May 30-31, 2015
URL: http://bos2015.opendatascicon.com/

## Speaker Notes

### DAY 1

**A. Keynote: Anthony Goldbloom**

- speaker: [Anthony Goldbloom](https://www.linkedin.com/in/anthonygoldbloom)
-"knowing something is possible makes it so"
	- the value of leaderboard on Kaggle, "data science as a sport"
- submission rate: ~100K/mo
- "feature engineering wins competitions"
	- you can't just throw models at the data
	- feature engineering matters more than algorithm choice
- Netflix Prize insight
	- "if you've already rated a movie that day, the next one you rate will be different than if you'd rated it first"
- keys:
	- good software engineering practices (version control, track errors)
	- robust statistical practices (correct regularization, cross validation)
- overfitting is a big issue in Kaggle competitions
- DS as "80% grunt work and 20% deep thinking"
- people are surprised by how much sharing happens on Kaggle
- most Kaggle competitors use Python, R, Julia
- ["scripts" feature](https://www.kaggle.com/c/titanic/forums/t/13390/introducing-kaggle-scripts):
	- you can run other people's code directly on Kaggle in a Docker instance
	- free for now
- most common backgrounds: statistics, computer science
- "our competitions choose us"

**B. Keynote: Josh Wills"

- speaker: [Josh Wills](https://twitter.com/josh_wills)
- "we have done a job of convincing the world that our job is terrible"
- data scientist: person who is better at statistics than any software engineer and better at software engineering than any statistician
- "if you aren't writing code that other people can use, you aren't a data scientist"
- data scientists:
	1. ask great questions
	2. answer them faster than anyone else
- airplane example:
	- standard question: "How do we build a man-powered plane?"
	- better: "How do we build prototypes that can quickly be rebuilt?"
	- able to try out way more ideas over two years than other teams
- Induced demand:
	- build another road to relieve congestion, reduce cost of driving, demand rises to the point where congestion returns to previous level
	- analogous to resource issue with everyone having Hadoop
- solution: "Mass transit planning" for data use infrastructure
- event series analytics: nested events --> multiple searches with no clicks in 3 seconds...early searches probably misspellings
- breaking your big database into little ones by user ID for massive parallelization
- as data scientists "we are not limited by our tools"

**C. Keynote: Ani Aghababyan, McGraw-Hill Education Analytics**

- speaker: [Ani Aghababyan](https://www.linkedin.com/in/aniaghababyan)
- edge = targeted, real time feedback
- predictive analytics --> "what correlates to what happeneded?"
- predictive modeling --> "what might happen?"
- prescription --> "what is the best that could happen?"
- open architecture --> importance of context, combinant data --> "whole picture"

**D. Keynote: Alex Cosmas, Booz-Allen-Hamilton**

- speaker: [Alex Cosmas](https://www.linkedin.com/in/alexcosmas)
- "will data scientists be extinct in 25 years?"
- KDN poll --> only 18.8% think we will "never" be extinct
- "advances in technology do not make science obsolete. They enable scientists to focus on the next big thing."
- "blind reliance on the mining of increasing volume of data is leading to (useless) information overload"
	- finding "snapple cap facts"
- "scientists seek truth"
	- it's a badge of honor to be a scientist
- we need theory to explore unknown/uncertain environments
	- "you can machine-learn the laws of physics. But that alone couldn't put man on the moon."
- don't focus just on tools
	- find a domain you care about --> "live the context"
	- "be the (physicist, biologist, marketer) who happens to be a data scientist"

**E. Democratization of Data**

- speaker: [Ari Hamalian](http://bos2015.opendatascicon.com/schedule/presentation-3/)
- "all of you create open data"
- Open Data:
	- accessible to all
	- machine readable
	- inexpensive (ideally free)
	- unrestricted right to use --> no licensing
- environmental factors cause asthma attacks
	- inhaler plays system with coordinates when you use it
	- generate heat map of danger zones
- Bretton Woods
	- World Bank, IMF
- Data.gov --> 130K+ datasets
	- execute order that data be machine-readable
- [Millenium Challenge](https://data.mcc.gov/) --> big public datasets
- USAID hackathons
- ["National Day for Civic Hacking"](https://www.codeforamerica.org/events/national-day-2016)
- "innovation works through information-sharing"
- "LAN Challenge Corp" --> web data, telecomm network science

**F. Making R Go Faster & Better"

- speaker: [Jared Lander](http://www.jaredlander.com/about/)
- three performance hurdles:
	- storage --> disk is cheap
	- computations --> Moore's law will handle this
	- memory --> most expensive thing (RAM)
- you can run R on Android
- solutions: compute intelligently
- aggregation
- htmlwidgets --> data.table (so cool)
- ["lahman" package](https://cran.r-project.org/web/packages/Lahman/Lahman.pdf) --> baseball data
- ```aggregate()``` function is really slow
- formula notation in R builds a matrix in memory --> this is slow
- ```tapply()``` is faster
- the gold standard is ```ddply()``` in the [plyr](https://cran.r-project.org/web/packages/plyr/plyr.pdf) package
- ["data.table"](https://cran.r-project.org/web/packages/data.table/data.table.pdf) package is blazing fast, but the notation sucks
- [dplyr](https://cran.r-project.org/web/packages/dplyr/dplyr.pdf) is highly recommended
	- really fast
	- Hadley's response to [data.table()](https://cran.r-project.org/web/packages/data.table/data.table.pdf)
	- currently single-threaded, but automatic parallelization version is coming
- [Rcpp](https://cran.r-project.org/web/packages/Rcpp/index.html) package is "fricken awesome"
	- run C++ inside R
	- crazy fast
- Parallelization:
	- [foreach](https://cran.r-project.org/web/packages/foreach/vignettes/foreach.pdf) package from Revolution
	- automatic parallelization
	- [DoParallel package](https://cran.r-project.org/web/packages/doParallel/vignettes/gettingstartedParallel.pdf) (Calls the right back-end for any OS)
- [microbenchmark](https://cran.r-project.org/web/packages/microbenchmark/microbenchmark.pdf) package
- speed (fastest first):
	- data.table
	- Rcpp
	- dplyr
	- tapply
	- plyr
	- plyr.parallel
	- foreach
	- aggregate
- what heppens when it doesn't fit in memoty?
- "A TB of RAM should be the new American Dream"
- [bigmemory package](https://cran.r-project.org/web/packages/bigmemory/bigmemory.pdf)
	- R objects that you can see, but they sit on disk
- [bigalgebra](https://cran.r-project.org/web/packages/bigalgebra/bigalgebra.pdf)
- [ff](https://cran.r-project.org/web/packages/ff/ff.pdf)
- you could use dplyr with databases
- [scidb](https://cran.r-project.org/web/packages/scidb/vignettes/scidb.pdf) package:
	- scientific DB
	- database-backed dataframe
	- looks like R objects
	- translates R into SciDB
- backends (still slower than in-memory)
	- bigmemory
	- ff
	- SciDB
	- dplyer backed by database
- computing:
	- data.table()
	- Rcpp
- [sqldf](https://cran.r-project.org/web/packages/sqldf/sqldf.pdf) only works for moderately-sized data
- speeding matrix:
	- Windows --> take algebra.dll and put in R
	- [pnmath](https://cran.r-project.org/web/views/HighPerformanceComputing.html)
	- change your matrix math library
- HDFS:
	- [RHadoop](https://www.mapr.com/sites/default/files/rhadoop_and_mapr.pdf)
	- [plyrMR](http://user2014.stat.ucla.edu/abstracts/talks/103_Piccolboni.pdf) for MapReduce
- RStudio has "performance profilers"
- jaredlander.com/talks

**G. Crowd-Sourced DS competitions"

- speaker: [Mark Higgins](https://www.linkedin.com/in/mark-higgins-63b0264)
- most data scientists are new to the field
- doing data science at an industrial scale is hard
- the talk is about companies whose "business is not data science"
	- NOT Facebook...more like McDonald's, JP Morgan
- competitions as a recruiting tool
	- hard to attract the best data scientists to these competitions
- [BattleFin](http://www.battlefin.com/) runs giant trading competitions
- [Quantopian](https://www.quantopian.com/) runs trading competitions
- code might now be portable:
	- languages used
	- packages
	- Methods for accessing data
	- details around execution
- ["elastic computation"](https://aws.amazon.com/ec2/)
- INSENTIUM --> Tiwtter sentiment analysis for equities
- Big Data paradigm --> "send the compute to the data"

**H. Feature Engineering**

- speaker: [David Epstein](https://www.linkedin.com/in/david-epstein-629a58)
- Scoure --> social media for identity verification
- TLDR --> "as we get better and better models, focus shifts to what you put in them"
- [feature engineering](https://en.wikipedia.org/wiki/Feature_engineering) = transforming data to create model inputs
- feature engineering $\neq$ feature selection
- trying to find the underlying data-generating process
- examples of common engineered features:
	- EBIDTA in finance
	- batting average in baseball
	- partisan performance in politics
- limits:
	- degrees of freedom issues
	- other variables enter your models as a controls, not really interested in functional form
- data science: care more about prediction than explanation
	- adding highly correlated predictors doesn't help
	- complex variables are less interpretable (tough sell to clients)
	- too much feature engineering can lead to overfitting
	- close connection between feature engineering and cross-validation
- "best" set of features? --> an [NP complete problem](https://en.wikipedia.org/wiki/NP-completeness)
- could include more if models do feature selection:
	- [LASSO](https://en.wikipedia.org/wiki/Lasso_(statistics))
	- [Logit](https://en.wikipedia.org/wiki/Logit)
	- [GBM with backward pruning](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3885826/)
- Lasso = "logit with penalization for complexity"
- LASSO eliminates variables, ridge regression just shrinks coefficients
- tree-based models are not affected by monotonic transformations of data
- [one-hot encoding](https://en.wikipedia.org/wiki/One-hot) = dummy variables
- "the hash trick"
	- hash up some text to make it into a number
	- non-numeric to numeric
- leave-one-out encoding
	- could lead to overfitting
- Andrew Ng:
	- scaling your data to be roughly the same range will improve the speed of regression estimation w/ Hill climbing
- interaction terms --> multiplication
- dimensionality reduction:
	- [PCA](https://en.wikipedia.org/wiki/Principal_component_analysis)
	- [Factor Analysis](https://en.wikipedia.org/wiki/Factor_analysis)
	- [clustering](https://en.wikipedia.org/wiki/Cluster_analysis) 
- model stacking --> outputs of one model become inputs of another
	- if you do this, use different data for different sets
- Next big advances won't come from new modelling tools
	- feature engineering is a big deal
	- domain experience is very important still
	
**I. Learning to Love Bayesian Statistics**

- speaker: [Allen Downey](http://www.allendowney.com/wp/)
- [slides](tinyurl.com/lovebayes)
- 5 myths of Bayesian stats:
	1. it isn't science because it's subjective
	2. it's hard and computationally intensive
	3. Bayes is redundant with classical methods
	4. We don't need it. 100 years of classical stats have served us well
- "They're subjective"
	- yeah but it's a good thing!
	- Bayes forces you to put decisions on the table
- "Unneeded because everything is great"
	- Iconnidis --> why most published research findings are false
	- Woolston --> Psychology journal bans p-values
	- Baker --> FIrst results from psychology's largest reproducibility test
	- Hypothesis testing, confidence intervals seriously flawed
- "Redundant"
	- classical --> CIs or point estimates
	- Bayesian methods --> [posterior distributions](https://en.wikipedia.org/wiki/Posterior_predictive_distribution)
	- [Ted Bunn's Blog](https://blog.richmond.edu/physicsbunn/)
	- [FiveThirtyEight](http://fivethirtyeight.com/) --> Nat Silver has been a public proponent of Bayseian stats
- "Slow"
	- slow compared to what?
	- these answer different questions
	- "[Bayesian Methods for Hackers"](http://camdavidsonpilon.github.io/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers/)
	- ["Think Bayes"](http://www.greenteapress.com/thinkbayes/thinkbayes.pdf)
- "Hard"
	- [learn Bayes with these pages!](tinyurl.com/compbayes14)
	- the math is hard, but it's easier to get if you approach it computationally
	- main idea --> u8se data to update beliefs
	- MacKay --> [Information THeory, Inference, and Learning Algorithms](http://www.inference.phy.cam.ac.uk/itprnn/book.pdf)

**J. Machine-in-the-Loop**

- speaker: Max Kleinman
- [coreference](https://en.wikipedia.org/wiki/Coreference) problem - lots of entities with the same name
- number of editors << entities ## mentions
- rate of assimilation (stuff you care about) << stream size (all stuff)
- [Trec KBA 2014 corpus](http://trec-kba.org)
- "vital" docs change entity profile, usually changing slot
- entity linker:
	- not just "filling in the sutff you know you should know"
	- ALSO --> give you new, exciting information
- human-in-the loop = active learning
- Diffeo --> accelearing curation of the knowledge base
- ["hierarchical clustering"](https://en.wikipedia.org/wiki/Hierarchical_clustering)
	- distantly supervised models
- Cross Doc Coref Resolution
- humans engage with search results sequentially:
	- ranking more important than sets
	- "crossing the set boundary might reveal the most interesting information"
- measurement: unexpected Expected Reciprocal Rank v-ERR
- go beyond keyword-based search --> deeper engagement
- groundtruth is expensive
	- if the system is able to learn actively, lower risk of your groundtruth becoming out-of-date and needing to re-do it
- crosswikis
- [memex project](http://opencatalog.darpa.mil/MEMEX.html)
- the goal: "your specific knowledgebase"
	
### DAY 2

**A. On-Demand Environments with Jupyter and IPN**

- humans learn through narratives
- reproducibility:
	- IPython/Jupyter
	- RMarkdown
	- version control (e.g. Git)
	- VMs
	- Docker container
- jupyter --> 26 languages (not just Python)
- JupyterHub --> muli-user option
- github.com/jupyter/jupyterhub
- Berkeley using this campus-wide
- set-up a Docker container with all the packages and dependencies
	- just give people the linke and each user gets their own turnkey server
- ["Python for Data Analysis"](http://shop.oreilly.com/product/0636920023784.do) - Wes McKinney
- beta.oreilly.com
- "Docker Jumpstart"
- Atlas platform:
	- semantic markup
	- transformation engines
	- version control
- adding Jupyter as an authoring option
- Docker - "containerizing the notebooks gave us a simple way to package up and deploy the content and all of its dependencies" 
- [tmpnb](tmpnb.org) --> create quick sandboxes
- Thebe plug-in --> minsk/singlecell
	- separates serving of static assets from the notebook
	- HTML widget that lets you drop in executable code
	- 34 different language kernels
	- run code inside the webpage
- github.com/jupyter/tmpnb
- Python ["Hydrogen" package](https://atom.io/packages/hydrogen)

**B. Dataframe: The Good, Bad, Ugly**

- speaker: [Wes McKinney](http://wesmckinney.com/)
- dataframe = "tabular data interfacer"
- Python
	- originally more for mathematical computing (i.e. MatLab replacement)
- dataframe is more of a user interface than data structure
- "big data is medium data collected over time"
- language ware are counterproductive:
	- shift developer focus to usability
- current state of DFs = tight coupling among:
	- User API
	- in-memory data representation
	- serialization/deserialization tools --> "conversion between formats"
	- analytics/computation
	- code evaluation semantics
- be wary of package performance benchmarks
	- "lies, damn lies, and benchmarks"
- strings aren't stored contiguously
	- really slow because you have to search all over memory
	- probably better to hash it
- map = key-value
- memory layout 1: columnar
	- faster for analytics
	- row appends harder
	- operations across rows hard
- memory layout 2: row-oriented
	- slower single-column scans
	- projections expensive
	- row appends easier
	- operations across rows faster
- CSVs are expensive to read and write
	- determining the schema is tough
	- you might lose precision
- R has limited support for nested type values (e.g. JSON structures)
- R uses special values to encode NA
- R issues:
	- copy-on-write semantics
- [pandas](https://en.wikipedia.org/wiki/Pandas_(software)) has strong time series support
- the dream: Apache-licensed, community standard C/C++ data frame structure and analytics toolkit we all use (R, Python, Julia)
	- interoperability with Spark

**C. Domain Expertise and Unstructured Data**

- speakers: [William MacMillan & Evan Schnidman](http://prattle.co/)
- "structure allows us to impose structure on otherwise unstructured data"
- lots of true things about the world can't be "easily vectorized"
- Prattle focuses on central bank communications
- Schnidman focuses on central banks academically
- "words are data"
- dictionary-based approaches are biased because they rely on pre-selected terms
- "central banks are great predictors of downside risk"
- used by some central banks to proof their language before release (e.g. to understand potential impact on equity markets)
- Prattle will have a weekly free version of the data soon
- Fed communications come out on Wednesday
	- "most appropriate response in bond markets not until Monday"
- the 12 regional Feds are private banks, shielded from FOIA requests
- people use 3rd-person language when relaying bad news
	- distnacing from bad news
- Reserve Bank of Australia as "best indicator of how Chinese economy is actually doing"

**D. Winning with Data Science**

- quant finance
	- data-driven trading strategies
- message: be a big fish in a small pond
- [estimize](https://www.estimize.com/) - crowd predictions of earnings estimates
- same approach with different data can succeed
- CO Everywhere - location-based social media information
- think breadth & diversity
	- don't do what everyone else is doing

**E. Hybrid Approach to Data Science Project Management**

- speaker: [Elaine Lee](https://www.linkedin.com/in/leeelainek)
- Civis Analytics --> spwaned from Obama-for-America analytics team
- Chicago-based consulting firm
- collaboration with "Github Issue Tickets"

**F. R & Neo4j**

- speaker: [Nicole White](https://github.com/nicolewhite)
- [Neo4j for R](https://neo4j.com/developer/r/)
- Neo4j is a graph databases
	- nodes with properties instead of fields and tables
	- can be queried as a graph
- ```RNeo4j::summary()``` shows all the node-node relationships
- try ```gvisSankey``` to look at co-occurrences
- igraph --> graph analytics library
- d3Network library for network visualization
- ```rstudio::Viewer(HTMLfile)``` to view HTML

**G. Robot vs Disease**

- speaker: [Shantanu Singh](https://sites.google.com/site/shantanu0singh/)
- [CellProfiler](http://cellprofiler.org/) = image analysis
- used machine learning to classify cells in slide images
	- "training classifiers", informed by human experts
- "signature" --> column averages of PCA principal components
- clustering to find groups of compounds that do similar things
- the clusters can reduce redundancy in screniing and speed testing cycle
	- think about Johs Wills' man-powered aircraft story

**H. Productionizing Deep Learning from the Ground Up**

- the goal --> "kill the deep learning hype"
- "Baidu & Google the only ones doing it"
- deep learning is basically neural nets
- pattern recognition on unlabeled and unstructured data
- for media/unstructured data
- automatic feature engineering
- benefits from complex architectures
- most NN are hybrids of multiple other types
- "this is fundamentally a software engineering problem"
- deep learning: way more layers
	- NN as hidden layers
- hyperparameters, loss functions
- "every NN is a different way of calculating the gradient"
- [recurrent neural nets](https://en.wikipedia.org/wiki/Recurrent_neural_network) --> time series NN
- memory networks
- adversarial architectures
- see work of [Laurens van der Maaten](https://lvdmaaten.github.io)
	- visualization for feature debugging
	- make it "not a black box"
- [project Adam](http://www.wired.com/2014/07/microsoft-adam/)
	- "microsoft gradient descent"
- [Google Brain](https://en.wikipedia.org/wiki/Google_Brain)
	- "generic-purpose ML project"
- special hardware required:
	- multiple GPUs
- data pipelines for this are not automated yet
	- file formats, sizes
- deep learning works well with diverse data
- scale hardware and software engineering are most important
- Hadoop/Spark not enough
	- GPUs not friendly to average programmer
- Production stacks:
	- many frameworks don't work well in a distributed environment
- grid search for neural nets (don't do it)
	- Bayesian, gradient-based approaches better
- scale your data
	- 0 mean, variance of 1
- "you use GPUs for training neural nets"

### TOOLS

**A. R Packages **

- [ff](https://cran.r-project.org/web/packages/ff/index.html): memory-efficient storage of large data on disk
- [bigmemory](https://cran.r-project.org/web/packages/bigmemory/index.html): shared memory and memory-mapped files
- [bigalgebra](https://cran.r-project.org/web/packages/bigalgebra/index.html): BLAS routines for big matrix objects
- [RNeo4j](https://cran.r-project.org/web/packages/RNeo4j/index.html): graph databases in R
- [D3Network](https://cran.r-project.org/web/packages/networkD3/networkD3.pdf)

**B. Tools**

- [Julia](http://julialang.org/)
- [Docker](https://www.docker.com/)
- [Spark](http://spark.apache.org/)
- [Pig](https://en.wikipedia.org/wiki/Pig_(programming_tool))
- [SQL](https://en.wikipedia.org/wiki/SQL)
- [MongoDB](https://www.mongodb.com/)
- [Cassandra](http://cassandra.apache.org/)
- [Hbase](https://hbase.apache.org/)
- [Exhibit](https://github.com/jwills/exhibit) --> "an evolving collection of various projects for executing SQL against things that look like tiny database tables"
- [PostgresSQL](https://www.postgresql.org/)
- [Scala](http://www.scala-lang.org/)
- [Caliper](https://www.imsglobal.org/activity/caliperram)
- [visual.ly](http://visual.ly/)
- [World Wide WEb Opendata Barometer](http://opendatabarometer.org/)
- [awk](https://en.wikipedia.org/wiki/AWK)
- [monetDB](https://www.monetdb.org/Home)
- [SQLite](https://www.sqlite.org/)
- [Google BigQuery](https://cloud.google.com/bigquery/)
- [HTML5](http://www.w3schools.com/html/html5_intro.asp)
- [pyCharm](https://www.jetbrains.com/pycharm/)
- [accumula](http://accumula.com/)
- [streamcorpus](http://streamcorpus.org/)
- [rejester](https://pypi.python.org/pypi/rejester/0.8.9)
- [jupyter](http://jupyter.org/)
- [Gitter Webhooks](https://developer.gitter.im/docs/services)
- [Remote SSH Spawner](https://github.com/jupyterhub/jupyterhub/wiki/Spawners)
- [Docker Spawner](https://github.com/jupyterhub/jupyterhub/wiki/Spawners)
- [Swarm Spawner](https://github.com/jupyterhub/jupyterhub/wiki/Spawners)
- [Ascii Doc](http://asciidoc.org/)
- [DocBook](http://www.docbook.org/)
- file formats:
	- [JSON](http://www.json.org/)
	- [Avro](https://avro.apache.org/)
	- [Thrift](https://diwakergupta.github.io/thrift-missing-guide/)
	- [Protocol buffers](https://github.com/google/protobuf)
	- [Parquet](http://blog.cloudera.com/blog/2013/03/introducing-parquet-columnar-storage-for-apache-hadoop/)
	- [columnIO](http://stackoverflow.com/questions/22745300/google-bigquery-underlying-architecture)
	- [recordIO](https://github.com/eclesh/recordio)
- [Haskell](https://www.haskell.org/) --> an advanced purely-functional programming language
- [Go](https://golang.org/) --> "an open source programming language that makes it easy to build simple, reliable, and efficient software"
