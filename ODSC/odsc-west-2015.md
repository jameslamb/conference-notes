# Open Data Science West (2015)

## Conference Details

Location: San Francisco, CA
Dates: Nov 20-22, 2015
URL: https://www.opendatascience.com/tag/odsc-west-2015/

## Speaker Notes

### PRE-CONFERENCE WORKSHOP: TEXT ANALYTICS

**A. Text Analytics**

- speaker: [Chris Mack](https://www.linkedin.com/in/christophermack)
- unstructured text
	- cement mixing
	- mine it, break it down, sort it, recombine it
- NLP = [Natural Language Processing](https://en.wikipedia.org/wiki/Natural_language_processing)
- HLT = [Human Language Technology](https://en.wikipedia.org/wiki/Language_technology)
- it is not:
	- machine translation
	- focused on structured data
- tasks:
	- categorization
	- sentiment analysis
	- entity extraction
- key package: ```python::NLTK```
- what matters?
	- never miss a possible answer
	- never show a wrong answer
- tradeoff --> recall vs specificity
- look for deeper measure than "right vs wrong"
	- precision
	- recall
- see ["Natural Language Processing with Python"](http://shop.oreilly.com/product/9780596516499.do)
- IPnotebook:
	- combine code execution, rich text, math, plots, rich media
- the text analytics project pipeline:
	- lots of building blocks
	- value increases as you progress, but errors amplify as you combine tasks
- [Cruft](https://en.wikipedia.org/wiki/Cruft) = content surrounding the comment you care about
1. Task 1: Acquire Text
	- identify the encoding
	- determine how many lines to read
	- biblical texts tend to have been translated into a LOT of language...so they are useful for some NLP tasks
2. Task 2: Determine the Language
	- downstream models ("Rules") depend on the language you have
	- use characters, encoding
	- use word choice, n-grams
	- see Python [langdetect](https://pypi.python.org/pypi/langdetect?) package
3. Task 3: Word Tokenization
	- using whitespace along will get you pretty far, but there are other subtleties to consider
	- normalizing --> [stemming](https://en.wikipedia.org/wiki/Stemming)
	- stems: spoken --> spoke
	- lemmas: spken --> speak
	- in search: "deal with the stemming issue at the point of index and at the point of search"
	- [WordNet](https://wordnet.princeton.edu/) --> lemmas, root dictionary
	- lots of publicly-available groundtruth
	- there are some statistical tools built into NLTK
	- less frequent words have most information
	- visualization idea: [lexical dispersion plot](http://www.nltk.org/book/ch01.html)
	- department of transportation has complaint text by manufacturer available
	- be careful about "normalizing out the signal you care about"
4. Task 4: Part of Speech (POS) Tagging
	- examining "the morphology of the sentence"
	- as you move to more complex stuff, open-source tools tend to be mostly English
	- POS-tagging can get very granular
	- big challenges: language ambiguity, POS ambiguity
	- use context to make informed decisions
	- probabilistic guesses aren't horrible either
	- broader lesson: context is your friend
	- multiple language in one text?
		- open source galls short here
		- maybe identify boundaries/language "chunks", apply language-specific rules within those?
	- overfitting is not a huge concern in text data
5. Task 5: Entity Extraction
	- entity - people, locations, brands, phone-numbers, part numbers
	- dictionary approach = premade list
	- common approaches:
		- dictionary = lookup
		- pattern = regex
	- chucking = entities, bits of text with some specific characteristics you care about
	- NLTK can produce a "parse tree" for you
	- don't ask questions as if 100% accuracy is possible...with text, it just isn't
	- be cautious about "changing things chasing a particular error case"
		- you should care about *where* errors are happening (i.e. broad classes of situations
6. Task 6: Relationship Extraction
	- disambiguation
	- coulde use concordance...look at words around the one you care about
- Summary
	- each step should be tailored to the task at hand
	- see [Stanford NLP](http://nlp.stanford.edu/)

### DAY 1

**A. Keynote: Project Jupyter**

- speaker: [Brian Granger](https://www.youtube.com/watch?v=GMKZD1Ohlzk)
- [numFOCUS](http://www.numfocus.org/: 501(c) 3 overseeing numPy and other parts of scientific computing ecosystem
- narratives:
	- computers are optimized for producing, consuming, processing data
	- humans? narratives/stories
	- [literate programming](https://en.wikipedia.org/wiki/Literate_programming) --> imbue code with meaning by wrapping them in narratives
- without the narrative, the data are meaningless
- [Jupyter](http://jupyter.org/) works with 40+ languages
- Jupyter notebooks render on GitHub
	- ipynb renders as static HTML on GitHub
- example: [data journalism on Buzzfeed](https://github.com/BuzzFeedNews/everything)
- using [Binder](https://github.com/binder-project), you can run notebooks hosted on GitHub
- check this out --> [spin up a quick notebook](https://tmpnb.org)
- tons of JavaScript coolness on [npm](https://www.npmjs.com/)
- new front-end for Jupyter:
	- real-time collaboration
	- multiple windows in one
- data science = identify the core questions
- shift your understanding away from the tools/skills & towards the questions
- See ["The Science of Why We Don't Believe Science"](http://www.motherjones.com/politics/2011/03/denial-science-chris-mooney)
- the *science* isn't hyper-technical paradigm:
	- it's the notion that we can learn by asking questions
- also this cool color thing --> [ColorHexa](http://www.colorhexa.com/)

**B. Keynote: Lukas Biewald**

- speaker: [Lukas Biewald](https://en.wikipedia.org/wiki/Lukas_Biewald)
- "data science ecosystem"
	- sources, wrangling, apps
- [Forrester](http://www.oracle.com/us/corporate/analystreports/forrester-wave-nosql-2348063.pdf) --> noSQL to grow 21% CAGR 2015-2020
- companies pay for data, open source algorithms
- Google, IBM, Intel, MIcrosoft opening up ML algorithms
- see [Code for America](https://www.codeforamerica.org/)
- getteing *better* data more important than *more* data
- automated cars taking over "in pieces" --> still a lot of human in the loop (HITL)

**C. Keynote: Philosopher's Stone**

- speaker: [Vin Sharma](https://www.youtube.com/watch?v=2PCEN93pCD4)
- [slides](http://www.slideshare.net/VinSharma1/open-data-science-conference-philosophers-stone)
- Big Bertha!
	- "stand on the shoulders of others"
	- stop building the same thing
- data science --> real science
- reproducibility is key
- re-usability is key
- "transmutation of data into value"
- the practice of turning data into insight should be open
	- stop re-inventing the same thing
	- leverage API economy
- "science friction":
	- one-off, ad hoc isolated models
	- application code, monolithic architecture, legacy components
	- single mode, single thread,
- AWS --> cloud scale infrastructure for fast development cycle
- turn DS to big data analytics: less alchemy, more chemistry
- build an open-source stack for cloud native app development
- infrastructure as a service:
	- provision data store you need as you need it
	- polyglot programming environment
	- key-val, document-oriented (e.g. [RDF](https://www.w3.org/TR/2004/REC-rdf-concepts-20040210/))
- spin up RStudio, IPython as needed
- most ML tasks can be broken into matrix algebraic functions
	- maybe, internally, break down these parts, use optimized version of each piece?
	- maybe even separate, optimized hardware?
- see [TrustedAnalytics](https://github.com/trustedanalytics)

**D. Emerging Field of Data Science**

- [data science subway map](http://nirvacana.com/thoughts/becoming-a-data-scientist/)
1. statistical thinking $\neq$ statistics
	- smell test
	- "does this make sense"?
2. technical skills
	- coding
	- data products
3. communication
	- translate abstract concepts into actionable information
4. curiosity
5. creativity
	- thinking outside of the box
6. grit
7. flexibility
	- most valuable skill
	- approach problems differently
- Master's Degree Path:
	- theory-rich learning
	- 9-20 month commitment
- self-taught (MOOCs)
	- self-guided learning
	- recorded lectures
	- no community, independent projects
	- self-driven job search
- Bootcamps (e.g. Metis)
	- experiential
	- learn from practitioners
	- 12 weeks
	- kind of a middle between M.S. & MOOC paths
- [Laurie Skelly](https://github.com/laurieskelly:
	- Andrew Ng philosophy --> "you can take one class and be able to apply machine learning to real problems"
	- don't be discouraged by "what you need to do data science" articles
	- you can do hackathons, meetups
	- big question: "are you willing to work with others?"

**E. Creating Data Driven Cities**

- speaker: John Reich
- "the future belongs to cities but we're not ready"
- city operating system:
	- connectivity
	- social
	- lots of data
	- smartphones
- see [USAspending](https://www.usaspending.gov/Pages/Default.aspx)
- predictive policing
	- some evidence that it works
- "open data by default"
	- see for example [City of Palo Alto](http://data.cityofpaloalto.org/home)
- go beyond disclosure
	- machine-readable disclosure
	- death to PDFs
- data science as a way to pull smart, ambitious people into civil service
- "see the invisible"
	- once you have the data, you can ask it questions
- think about different levels of "have"
- another example: Boston "adopt a fire hydrant" program
- write code for other people's consumption
	- modularize EVERYTHING
- "STEAM" = STEM + art
- goal: "create a new OS for data-driven cities"

**F. Julia's Place in Data Science**

- speaker: [Drew Conway](http://drewconway.com/), author of [Machine Learning for Hackers](http://shop.oreilly.com/product/0636920018483.do)
- Julia "statically compiles at runtime"
- normal compiler is checking lots of crazy possibilities
	- e.g. "have you redefined what 0 is?"
	- Julia says "meh"
- Julia translated into machine code that is a factor of $10^{6}$ smaller than equivalent R
- Julia is best at "modeling computations" e.g. [SVD](https://en.wikipedia.org/wiki/Singular_value_decomposition)
- weakly structured --> tabular data --> array data
- array --> vectors, matrices, [tensors](https://en.wikipedia.org/wiki/Tensor)
- Julia makes fast machine code by proving consistency
- Base Julia sucks for dataframes, but "awesome" for arrays
- weak structure --> arbitrary types, bad metadata
- tabular --> arbitrary types, good metadata
	- Julia is worst at this
- array --> consistent types, no metadata
- progress to Julia 1.0:
	- native multithreading (Intel)
	- string representation rewrite
	- garbage cleaning improvements
	- doc system improvements
	- better support for multiple types
	- array representation
	- type system fixes for function types
- [hardware acceleration](https://en.wikipedia.org/wiki/Hardware_acceleration) --> the use of computer hardware to perform some functions more efficiently than is possible in software running on a more general-purpose CPU
- "singular instructor, multiple data"

**G. PySpark Best Practices**

- speaker: [Juliet Houghland](https://www.youtube.com/watch?v=zHcwyKjc09M)
- Spark --> framework for distributed computation
	- runs on Java virtual machines (JVM)
- driver program, worker nodes
	- 1 "task" = 1 partition
- Spark is written in Scala
- "one of the most exciting things is the language wrappers"
- Py4j lets you pass data back & forth between a JVM
- passing Python function --> ["pickling"](https://docs.python.org/2/library/pickle.html)
- using dataframes avoids "serialization penalty"
- read-eval-print-loop ([REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop))
- always write shareable code
- structure:
	- parse CLI args and configure Spark app
	- data I/O
	- turn data into features
	- fancymath with Spark
- it is useful to separate data I/O from analysis
- write testable code
	- separate feature generation of data standardization from modeling
- make your functions static
- Spark is meant to be an [in-memory system](https://www-01.ibm.com/software/data/what-is-in-memory-computing.html)
- write serializable code:
	- use static methods
	- "functions and the context that is needed to execute must be serializable"
- writing PySpark much easier than running it
- [Spark testing base](https://github.com/holdenk/spark-testing-base)
- consider adding weird cases to a running test-case file
	- keeping this running list captures edge cases, lets you progress
- running distributed code is really hard
- [YARN](http://hortonworks.com/apache/spark/)
- think about raising errors in the right place:
	- "earlier exceptions are more relevant than later ones"
- be careful about dependencies
- scit-kit learn works on a single node
- Hadoop is made for "commodity hardware"
- goood performance from Spark requires a lot of RAM
	- hard to know how the cluster should look
- Spark should run on any hardware
- Spark is being used more in iterative machine learning work
	- recovery model makes it tough for large-scale ETL
	- complex ETL logic is harder in Spark
- "Scala has stricter type-checking"

**H. Data Science at Home Depot**

- speaker: [Huiming Qu](https://www.linkedin.com/in/huiming-qu-b824004)
- HD "Augmented Reality"
- logged-in users vs. "identifiable visitor"
	- vs. unrecognized visitors
- low-hanging: "frequently bought together"
	- need to set a threshold?
	- have some rationale for recommendations
- conduit --> where do you personalize?
- Home Depot purchases third party data to match individuals' records

**I. Anomaly Detection at Netflix**

- speaker: [Chris Colburn](https://www.youtube.com/watch?v=xjHlu9OViVc)
- at peak, 1/3 of global downstream internet traffic is tied to Netflix
- goal: "fully global" by end of 2016
- on Netflix:
	- ~40 code pushes/day
- Netflix is a huge AWS shop
- Hadoop users at Netflix as well
- "vast number of companies moving away from Hadoop toward Spark"
- Hadoop but not HDFS --> AWS instead
- tools:
	- [Hadoop](https://en.wikipedia.org/wiki/Apache_Hadoop)
	- [Kafka](http://kafka.apache.org/)
	- [Python](https://www.python.org/)
	- [Presto](https://opensource.com/business/15/3/three-open-source-projects-transform-hadoop) (For "interactive queries")
	- [Teradata](http://www.teradata.com/?LangType=1033)
	- [Tableau](http://www.tableau.com/)
	- [Cassandra](http://cassandra.apache.org/)
- Presto:
	- reuses JVMs, no latency from spinning up new ones
- A/B testing framework running in [Druid](http://druid.io/)
	- fast but rigid
- Ursula aggregates small files within a partition
- Hadoop naturally ahs the idea of metadata in file headers
- [METACAT](https://knb.ecoinformatics.org/knb/docs/index.html) + some big data API
- what is anomaly detection?
	- you have a bunch of arbitrarily large matrices
	- hash any size into 10x10
	- also: RSVD/RDCA (matrix decomposition)
	- steps:
		 1. start with simple SVD
		 2. decrement singular values by some threshold
		 3. calculate residual
		 4. threshold the error
	- PCA is SVD of a covariance matrix
	- correspondence analysis
	- ARIMA --> robust realization systems
	- ARIMA has the same issues regression has
- See the [NetFlix Tech Blog](http://techblog.netflix.com/)

**J. How Big Data + CUstomer Intelligence Have Revoluationized Retail**

- "intent beats demographics"
- big data isn't intelligent...it's big
- domain experts define the problem, engineers solve it
- how you win kaggle:
	- preprocesses the data
	- build features
- almost always better to build features:
	- ratios are hard for computers to solve
- "build features to collapse information into one record"
- problem: too many high cardinality categorical variables
	- ignore them or bin them manually
- decision trees are greedy searchers (they never go back):
	- can get stuck on bad paths
- game changer --> more affordable processing via the cloud
- the algorithms are not game changers:
	- all about the data
- this is why you see firms open-sourcing algorithms...the money is in the data!
- key takeaway: build lots of features!


### DAY 2

**A. Ibis**

- speaker: [Wes McKinney](http://wesmckinney.com/)
- "scaling Python Analytics on Hadoop and Impala"
- Python is a "standard language of data science"
- main use case = data science and engineering swiss army knife on small-to-medium size data
- Python is confined to single-node analysis today
- normal flow:
	- get arbitrary JSON
	- put it in S3 of some file system
	- do stuff
- pandas:
	- trying to bridge gap between industry analytics and scientific programming
	- "an imperfect, in-memory dataframe"
	- only supports flat data
	- built using Python's scientific computing stack
- [Amazon Redshift](https://aws.amazon.com/redshift/)
- general trend in data science tools:
	- SQL as UI...a way to describe computaiton
	- DBs convert SQL into a data plan
- Hadoop
	- decouple storage (HDGS) and compute (MapReduce)
- data ingestion --> [Kafka](http://kafka.apache.org/)
- Scala/Java for MapReduce
- Analytic SQL
	- major trend toward being able to analyze JSON in place
	- no need to push to star schema
- Ibis: a "Python-on-Hadoop" experience
	- remove SQL from user workflows
	- develop high performance Python extension APIs
- SQL is hard to refactor
	- not easily composible
- [IBIS project](http://docs.ibis-project.org/sql.html)
- use IBIS API as UI layer, ibis converts expressions into SQL for Hadoop
- IBIS: have same function call map onto different DB back-ends
- IBIS/Impala
	- complex types support
- user extensibility with native performance
	- in-memory columnar format
	- Python-to-LLVM IR compilation
- "compute engines written in C/C++ of Java/Scala"
- external UDFs
	- implement in user language through some external language protocol
	- slow: serialization overhead
	- slow: scalar vs vectorized computations
	- slow: RPC overhead
- make this faster
	- common data representation in-memory
	- stnadardized in-memory columnar (IMC)
	- IMC-for-SQL: Apache Drill
- DFS = "distributed file system"
- see [Cloudera blog](http://blog.cloudera.com/)
- IBIS vision --> Python end-to-end at any scale

**B. Speeding up R on a Distributed Hypervisor**

- [TidalScale](https://www.tidalscale.com/)
	- put Big Data in-memory
- today's scale-out model
	- chunk out the job
- hypervisor
	- a "virtualization" layer that handles managing many nodes
- locality principle
- cVPU = virtual CPU
	- "floats across cluster"
- read: ["Computer Architecture"](https://www.amazon.com/Computer-Architecture-Fifth-Quantitative-Approach/dp/012383872X)
- no API --> it "just works"
- this is a "rack-level" solution
	- put a bunch of hardware together, boot as a single machine
- the idea is that you can scale up to huge sizes with commodity hardware
- distributed in-memory computing is hard to do well
- the goal is to get linearity in performance with respect to input size
- R hits a "memory cliff" where it starts "paging" with memory
- this is a tool that is useful for cases that are not easily parallelizable
	- observations are interdependent
- the TidalScale solution:
	- no need to parallelize at the application level
	- just compile a rack of servers and run any job you want
- "the larger the single machine, the finer patterns you can see"
- TidalSCale has 3 POC systems available for testing
- you get "All of the resources"
	- more external ports, DVD-ROM, etc.
- on-premise
	- virtualization "on the hardware"

**C. Prattle Analytics**

- text analytics watching central banks
- data science buried "deep" in organizations
- history of stats and machine learning:
	- formalizationof decisionmaking
- rapid GDP forecasting ("nowcasting")
- nowcasting
	- breaks national accounts structure
	- adapted for sporadic data
- don't be afraid to take partial entries
- CB communication --> not a pure "Data science" solution
	- [greenspan briefcase watch](http://money.cnn.com/1999/06/29/economy/fed_briefcase/)
- "words are data"
- experts are biased
- simple text analysis dictionaries don't work for Fed speak and complex language
- post hoc hedging = trade right after policy
- decent correlation to large cap equities too
- takeaway:
	- decentralize teams, combine expertise
	- create models to fit the application
	- allow DS to be a tool for action, not just guidance

**D. Data and Data Science for Social Good**

- speaker: [Steve Mills](http://www.boozallen.com/careers/meet-our-people/steve-mills)
- DS: data --> insights --> action
- data science can change the world
- "a small group of computers with access to data can have a huge impact on the world"
- holocaust --> "early warning"
- "data science can change the world"
- "imagine what 10 data scientists in a room on a Saturday can accomplish"
- 6 months --> average age in U.S. at digital birth
- 87% of US could be uniquely identified by 5-digit zip, gender, DOB
- 90% of credit card users can be uniquely identified by 4 points
- anonymized $\neq$ anonymous
- we want the ability to control our own data
	- sell it?
	- protect it?
	- share it for social good?
- maybe use blockchain as the main tool
	- share info while maintaining control privacy
- big questions: what would you be willing to share?
- www.boozallen.com/data-science
- www.boozallen.com/data-science-field-guide

**E. Public Sector Credit Solutions**

- speaker: [Marc Joffe](https://www.youtube.com/watch?v=k_Q_Nj48BIk)
- there is no comprehensive national repo for files and they are all in PDF format
- db of "CAFR database"
- the goal
	- better measures of risk
	- early morning signs pre-default
- www.pdfliberation.wordpress.com
- tools:
	- [Able2Extract](http://www.investintech.com/prod_a2e.htm)
	- [Tabula](http://tabula.technology/)
- [House Resolution HR2477](https://www.congress.gov/bill/114th-congress/house-bill/2477/all-info)
	- Darrell Issa
	- bill to mandate machine-readable disclosure (like XBRL)

**F. Machine Learning and Data Science projects with Python and H2o**

- an open-source toolkit for machine learning and data management
- everything is parallel and distributed
- you can move your model out as a Java object for scoring new samples
- Rob Tibshirani is an adviser
- "one-hot encoding"
- PySparkling Water = Python + Spark + H2o
- h2o.ai/download
- learn.h2o.ai --> IoT example

**G. How Companies are Using Tachyon**

- "one of the fastest-growing big data open source projects"
- critical role in data lake archi
- crticial role in data lake architecture
- [Tachyon ](http://conferences.oreilly.com/strata/stratany2014/public/schedule/detail/36342) used to pass data between file systems
- [GlusterFS](https://www.gluster.org/) file system
- Tachyon as "distributed cache"
- default storage for Spark
- main idea: keep data close to where computation happens
- Tachyon manages more than RAM
	- "configurable storage tiers"
- you can now mount different file system in a different path in Tachyon
	- HDFS clusters, S3 buckets
- resource managers - mesos, Yarn
- "Machine Intelligence Lanscape"

**H. Data As a Culture**

- speaker: [Jon Eduald](https://de.linkedin.com/in/jonedvald)
- data warehouse hosted in RedShift
- "Data should permeate the business"
- responsibility and ownership are important
- data science sitting under COO
- DS supporting other teams by teaching, not doing
- advice: "adapt and evolve"
- don't make event tracking an after thought:
	- think about when you want programs to fail
	- conduct unit tests
- empower people to use data, educate them
- take the time to proactively demonstrate the value of data
- themes/human factors:
	- organization
	- responsibility
	- motivation

**I. Does Code Quality Really Matter?**

- speaker: [James Powell](https://twitter.com/dontusethiscode)
- key: "other people's code is bad code"
- readwatch - breakpoint every time a variable is accessed
- "goode code is code I wrote, abd code is code you wrote"
- code reviews are purely political
- unit tests are bureaucratic, not scientific
- "most code is an artefact of some business process"
- encoding is "spelling"
- see [Python metaclasses](https://jakevdp.github.io/blog/2012/12/01/a-primer-on-python-metaclasses/)
- it's tautological to say code matters when it does and doesn't when it doesn't
- "some encodings are better for human understanding"
