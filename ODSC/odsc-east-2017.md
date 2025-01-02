# ODSC East
Boston, MA

## Day 1

**A. Challenges and practical solutions in successful developing and delivery of data science applications**

Speaker: Ali Marami, RBrain

- https://r-brain.io/en/
- Jupyter Lab - integrated environment w/ different language kernels
    - https://github.com/jupyterlab/jupyterlab
- IT vs. developer conflict:
    - devs want root access
    - IT wants stability ,security
    - solution: containers:
        - let people do whatever the fuck they want in Docker
        - VMs are heavy (not built for collaboration), server-based IDEs can get overwhelmed
- mentions Shiny, Bokeh as deployment solutions
- Container scales in a more "sophisticated" way
    - security, access control is easier with a container
- how containers work:
    - wrap a piece of software in a complete filesystem that contains everything needed to run
    - includes code, runtime, system tools, system libraries
    - "with containers, we killed localhost"
- migration to cloud using containers:
    - you have to build and maintain images
    - installation of system libraries in the containers
    - containers orchestration
    - deployment
- GitLab = build a full development environment
- what do they do:
    - you build a GitLab IDE on top of prefab containers
    - you can package up your application and send it out as a container

**B. Precision agriculture: Predicting outcomes for farmers using machine learning to help feed the world**

Speaker: Jeff Bradshaw, founder at Adaptris

- we need to evolve agriculture more in the next 25 years than we have in all of history
    - based on productivity, population growth
- "2/3 of variance in yield comes from factors that we can influence" (not weather)
- many systems on farms super old
- "everyone is excited about using satellite, drones"
- seed:
    - you have six weeks to sell seed
    - but you don't know until the start what you'll actually have
- "every cow in the UK has a passport"
    - https://data.gov.uk/data/search?q=twins+born
- tractors:
    - a single tractor throws off 30MB of data a day
    - all tractors throw off 160GB a day
    - biggest challenge is "combining that data with other farm data"
- the CMA equivalent in agg is called an "agronomist"
    - a "plant doctor"
- "growers are really rubbish at data entry"
- this is a space that data still has not successfully penetrated
- this company has already touched tons and tons of agg companies:
    - dupont
    - monsanto
    - ADM
- "I find that the mobile network is actually better in Africa than it is in the U.S."
    - copper wire was getting stolen, so they went straight to the mobile network route
- there is of course some element of "you're telling me things I already know"

**C. How to Build Fully Automated QA System for a Large Scale Search Engine**

Speaker: Khalifeh AlJadda, Lead Data Scientist at CareerBuilder

- Information Retrieval = finding material of an unstructured nature that satisfies an information need from within large collections
- main model in IR = "vector space"
- "recommendation" = "leveraging context to automatically suggest relevant results"
- relevancy measure = F1 score (combines precision and recall)
- a better measure that accounts for position too:
    - "Discount Cumulative Gain" (DCG)
    - requires a labeled dataset
    - NDCG = normalizes DCG between 0 and 1 (0 is terrible)
- relevance = clicks/(click + skip)
- stack used:
    - Spark
    - Solr
    - Ooozie
    - HDFS
    - Hive
    - Sqoop
    - Tableau
- Sqoop:
    - efficiently moving data between Hadoop and relational DBs

**D. Selling Flowers with Analytics**

- dutch flower auctions...completely digitized
- crazy complicated math being applied to this very conservative industry:
- some projects:
    - "what is the minimum purchase quantity?"
- dutch auction = you only have winning bids

**E. Data Science lifecycle with Apache Zeppelin**

Speaker: Moon soo Lee, founder of Apache Zeppelin

- web-based interface for notebook DS using Spark, SQL, etc.
- one notebook for all:
    - data engineer (ETL)
    - data scientist
    - business user
- you can define arbitrary blocks in deferent integrations, like this:

```
%python
print('python')
```

or

```
%spark
some_spark_stuff
```

```
%sql
select * from bank limit 100
```

- so Zeppelin has an engine for deciding how your output gets formatted
- you can share out this same notebook to business people
- data engineers, data scientists, biz people can collaborate in one doc
- syntax is as easy as `%[python]`
- visualizations:
    - there are some built-ins
    - there's also an add-on bundled package called "Helium"
- Zeppelin users can upload viz components to npm
- Zeppelin has a cron-like scheduler so you can schedule notebook to re-run on a fixed schedule
- support for multi-user interaction
- default:
    - session is broadcasted across all users
    - changes reflected in real time
    - "collaoration mode" vs. "personalized mode"
- Zeppelin supports interpreter
- friends of Zeppelin:
    - ZEPL
    - ZEPL on Amazon EMR
    - HDP from Hortonworks
    - Zeppelin on Microsoft Azure
- Apache Zeppelin big idea: notebook that combine a bunch of backends fluidly and enable collaboration
- Zeppelin does not have an official Docker image
- Zeppelin is simple:
    - one daemon process
    - you connect over your browser
    - using Python, R probably fine in Docker but distributed stuff like Elasticsearch, Spark would be really hard
- cluster mode is coming (os you'll be able to distribute interpreter process across a cluster)
- takeaway: we should be using Zeppelin yesterday. Whoa
- remember:
    - https://zeppelin.apache.org/docs/0.6.1/interpreter/elasticsearch.html

**F. Building a Near Real-time Data Pipeline in the Cloud**

Speaker: Daniel Stair & Lovan Chetty, Cazena

- some needs:
    - load in about 10GB per day
    - ETL jobs running alongisde analytic workloads
- used Oozie for job scheduling:
    - files hit the webHDFS REST API
    - Spark SQL does various ETL stuff on the files, writes out to Parquet
        - (Parquet is faster for ad hoc queries)
    - Impala runs to build final table
- Python script drives every part of the ETL process
- some tuning:
    - testing time on source data on HDFS vs. source data on blob store
- remember:
    - Spark will only do what you tell it
    - you need to optimize your application-level Spark job to appropriately take advantage of parallelism
- make sure your infrastructure is not just optimized for one use case
- think about file types:
    - Parquet for Impala
    - Orc for Tez
    - JSON for Apache Drill
- you can make your cloud a private croud:
    - mandatory encryption in motion and at rest
    - only private IP addresses
    - role-based access control with Active Directory
    - still log and audit things

## Day 2

**A. Privacy Techniques for Data Science in Regulated Environments**

- idea of "differential privacy"

**B. Evolutionary Search for Modeling and Forecasting**

Speaker: Michael Schmidt, CTO, Nutonian

- Eureqa: software for evolutionary search powered by AI
- http://www.nutonian.com/products/eureqa/
- evolutionary search:
    - more computing resources means you can explain transition effects
    - "get compact, explanatory models for how things really work"
- where to use Evolutionary Search: NP-hard computational problems
    - you know what you want, but not how to solve for it
        - no gradient
        - exponential search space
        - local optima
- challenges:
    - evolutionary search requires tons of computational resources
    - no viable open-source frameworks
- steps in evolutionary search history:
    - genetic algorithms (John Holland)
    - Genetic Programming / Symbolic Regression
    - self-modeling, dynamical systems
    - explanatory modeling
- could use evolutionary search to automatically find right lags, window sizes
- you can find nonlinear effects:
    - impacts have conditional dependencies and coupled effects
    - need to engineer predictive features
- evolving models for your data:
    - generate candidate models
    - efficiently permute their structures
    - test their hypotheses against the data
- you can test out "hundreds of billions of hypotheses"
- you also look at the complexity of the model
- it is hard to optimize for simplicity
- Eureqa allows you to incorporate prior knowledge and constraints
    - traditionally a hard thing to do in machine learning
- IoT models for predicting failure conditions
- most common users are engineers
- some companies that use it:
    - RioTinto
    - GE
    - Autodesk
    - Honeywell
- main motivation: "there are tons of problems that have strong signals you can find, you just need the right way to encode them"
- "if you try to use all the sensors at once, it is easy to overfit"

**C. Creating and Preprocessing a Design Matrix with Recipes**

Speaker: Max Kuhn

- the "design matrix" = RHS
- functions can be embedded inline to do fairly complex things (on single variables) and these can be applied to new data sets
- formula notation means everything gets embedded into the design matrix:
    - like if you try to run `knn_impute`, you are going to be storing the entire matrix of neighbors (potentially one per variable that you are imputing)
    - you cannot have nested inline function
- the formula framework was designed when nobody though that we might have hundreds or thousands of predcitors in the model
- model saves the formula information very inefficiently and it can impact performance
- above like 1000 features, you spend more than half your time creating the design matrix
- ways people have "bastardized" formula model to account for other roles for variables:
    - `lme4::lmer`
    - `BradleyTerry2::BTm`
    - `mboost::mob`
- variables can have many roles:
    - outcomes
    - predictors
    - stratification
- `recipes` package
- example:

```
rec <- recipes::recipe(price ~ type + sqft, data = Sacramento)
rec <- rec %>%
    step_log(price) %>%
    step_dummy(type)
rec_trained <- learn(rec, training = Sacramento, retain = TRUE)

design_matrix <- process(rec_trained, newdata = Sacramento)
```

- "R was originally written as a set of Fortran wrappers"
