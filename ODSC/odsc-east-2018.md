# ODSC East
Boston, MA

## Day 1

**A. Keynote: Drew Conway**

- 2004-2015 = "Jeff Goldblum era of Data Science"
- "i take a lot of responsibility for the fact that the venn diagram got interpreted as describing a person"
- interviewing data scientists:
    + doing the take-home is just the entry fee to get an interview.
        * "I have rarely seen a take-home that's directly connected to the interview or the work itself"
    + "live coding is great interview technique because it sucks"
    + "your interview is a product of your team's culture"
    + be transparent...you want people to feel comfortable coming to work for you. Being transparent (including)
- he works at a company called Alluvium now
- tips for interviewing:
    + write a really specific job requirement. Don't be cryptic
    + build the take-home exercise
        * should look exactly like what you'll do at work
        * "we built a streaming service with real data in it for people to use in the take-home"
    + phone screen
        * answer candidate's questions about us
        * do this AFTER the take-home
    + send take-home
        * package it in the tools you use
        * we use a repo and people make a PR into it
    + in-person:
        * meeting 1: code review
            - pair with dev and/or data science
            - live code review: question approach, understand logic
        * meeting 2: project planning
            - create new requirements from the take-home
            - how does a candidate take ownership?
        * meeting 3: project discovery:
            - deep technical dive on proposed project
            - like a pre-mortem
        * meeting 4: the culture interview
            - asking questions driven by customer values
- post-interview review:
    + "consensus no-hire"
        * they take this as a failure of the process and a waste of time
        * use it to learn what they could have seen earlier to avoid this
    + "consensus hire"
        * all went well, make the offer
    + "need more information"
        * occasionally the team will try to bring the person back and ask for more
- the final step is actually closing the candidate
    + "good people have a lot of offers"
- GREAT POINT: if you can tell people exactly what work they'll do and get them excited about it, it can help you win them away when they have competing offers

**B. Keynote: Cathy O'Neill**

- "if you ask Google if the Holocaust is real, you get 10 holocaust denial sites"
- we obscure the subjectivity of DS behind math
- algos as WMDs
    + Widespread
    + Mysterious
    + Destructive
- "I applied for a DS job recently and they tried to make me do a take-home and I was like fuck you I'm not doing that"
- case study:
    + there have been scandals recently at Fox news re: gender discrimination and harassment
    + now imagine you were hired to build a hiring model to help Fox News
    + you might look at the last 20 years of hiring and define it as a supervised problem. Maybe the target is "stayed for 4 years and got promoted"
    + data science is just going to learn the biases that existed...it's going to
- on crime:
    - only around half of murders lead to arrests
    - reported crimed != crimes
    - "think about what it would look like to actually have crime data in this country"
        + you'd need surveillance in every room in every building
        + some communities live in a world closer to this (like very poor communities) and the rate of arrests-per-crime is much higher for them as a result
- there is no "FDA for algorithms"
- "you don't have privacy rights when you're a criminal defendant or teaching at a public school"
    + basically, don't confuse this as just a talk about privacy problems
    + this is about predatory or prejudiced automated policymaking

**C. Industrial Machine Learning**

- Josh Bloom, GE
    - Professor @ UC Berkeley
    - VP Data and Analytics, GE Digital
- "I'm not gonna be selling you any GE products unless you want to buy a wind turbine"
- personal background
    - "Fork me on Github"...hell of a pitch lol
    - He started wise.io
    - co-founder of Berkeley Institute for Data Science (BIDS)
- "experts do not scale"
- the pitch for Wise.IO:
    + tickets come in from customers
    + auto-answers are sent back to customers only if model confidence about the inferred meaning and steps to resolve were high
    + lower-confidence flagged something for manual intervention
    + "we added a random amount of time to response so it seemed like you were getting a bespoke email just for you"
- it's important to have some fault tolerance at the UI layer in case your backend system goes to hell
- changed the language on all his slides from like "smart city" to "brilliant city", "brilliant factory", etc.
- obligatory "number of connected devices" and "zettabyes of data" slide. Gotta love it
- what we do at GE isn't IoT, but "the internet of really important things"
- things he listed:
    + preventative maintenance
    + failure/anomaly detection
    + assistive diagnosis and treatment
    + systems optimization
- made a kind of petty comparison between industrial DS vs. consumer DS
    + though the point is valid
- "in our world, we can't be wrong"
    + https://www.slideshare.net/JuneAndrews/counter-intuitive-machine-learning-for-the-industrial-internet-of-things-77853709
- physical models:
    + captures a priori understanding of device / system
    + doesn't require data
    + params are interpretable because they have physical meaning
    + you can simulate things that you've never seen in the historical data
    + it's really hard to bake non-physical metadata into the physical model (like who the operator is)
- data-driven models:
    + no need to understand the physics
    + they're extensible
    + they learn from data
    + not interpretable
    + generalizability outside of data you've seen is questionable
- how to marry physics and data driven models for IML:
    + use physical models as an input
    + Reinforcement learning
        * transfer learning with updates in the real world
    + try building networks with physical constraints into models
        * CV: GVNN (Handa)
        * "QCD-Aware Recursive NN for Jet Physics"
    + KEY POINT: you could use a physical model and then use data-driven approaches to explaining the residuals from the physical model
- "only 1000s" of failures
    + 0_o
- https://github.com/bnaul/IrregularTimeSeriesAutoencoderpaper
- IML results need to be presented in a way that's understandable
- You need to surface the "why"
- he showed a color drawing of an engine with anomaly alerts pointing to components
- obligatory GDPR slide
- Privacy & Security of Industrial Machine Learning
    + he showed a picture of a nuclear power plant to try to look cool
    + some papers:
        - "Differentially private GANs as a surrogate for Data sharing"
        - "machine Learning classification over encrypted data"
- Open-source parallel text reader:
    - github.com/wiseio/paratext
- Open Source
- noted the importance of Open Source to what GE Digital is doing
- GE funding:
    + Ray + Plasma
    + Clipper
    + Alegro
    + Arx
- "Machine Learning: The High Interest Credit Card of Technical Debt"
- ML and algorithms are a very tiny piece of the code that people actually use
    + 95% is "glue code"
    + putting ML into prod opens you to technical debt of a form that most software engineers are not used to dealing with
- final takeaway:
    + compute and algorithms are becoming commoditized
    + unique data and domain expertise are much more important and more valuable
    + creating even tiny efficiency gains can have a huge bottom-line impact

**D. The past, present, and future of automated machine learning**

- Randy Olson
- "AutoML is a quiet revolution in AI"
- automating the process of applying machine learning to data sets
- footnote: "image source: spurious extrapolation. Don't do this at work. Seriously."
- ML still requires a lot of manual programming...autoML is hard
- "default parameters are almost always bad"
    + took 13 algos from scikit
    + tried various experiments with them
    + pulled together as many classification datasets as possible, then tried to analyze distribution of improvements to CV scores from tuning (diff between random other params and using the scikit learn defaults)
- AutoML will do parameter tuning for you, so that's cool
- "we should never assume that one algorithm is going to be the best one for the problem"
- AutoML handles that too
- AutoML is a productivity tool, not a replacement for data scientists
- parameter tuning:
    + most people use random search and grid search
    + this isn't really autoML
- what autoML handles:
    + picking an algorithm
    + picking hyper-params
    + some aspects of data cleaning
- "modern AutoML"
    + very very large search spaces require smarter optimization
        * meta-learning
        * bayesian optimization
        * genetic programming
        * multi-armed bandit
- TPOT --> an autoML framework in Python
    + https://github.com/EpistasisLab/tpot
- DataRobot's crazy nonsense also has an autoML solution
    + it will show like a leaderboard of combinations that are performing best
- open source tools:
    + auto-sklearn (python)
    + auto-Weka (Java)
    + TPOT (python)
    + h20.ai autoML
        * really nice web interface
    + devol (python)
- commercial autoML tools:
    + DataRobot
    + H2O.ai Driverless AI
    + Google AutoML
- AutoML in the near future:
    + autoML will also handle most of the data cleaning process
        * unstructed --> tabular
        * capture and automate human approaches to data cleaning
    + autoML will vastly improve deep learning
        * automated DNN architecture design
        * automated preprocessing of data prior to modeling
    + autoML will scale to large datasets
        * autoML is very slow right now on "Big Data"
        * Spark, dask, TensorFlow, etc. will help bring AutoML to scale
- autoML is actually going to expose the need for people who can "think like a data scientist"
    + collecting and curating the right data
    + thinking like a data scientist
- meta-learning is about automating the automation of automation
- autoML slides (kicks off a download) --> bit.ly/2HS01Rr

**E. R Packages for Team Collaboration**

- speaker: STEPHANIE KIRMER!!!
- note to self:
- "I'm not going to dictate THE single way to write R packages or structure your DS workflow"
- DS teams without structured, intentional collaboration leak knowledge and waste resources
- "I'm proposing we steal tools from software engineering for how you do data science"
- ahhhh she showed the UptakeOpenSource page!
- made the great point that you can actually show off this professionalism around code management to new candidates to convince them that your org is legit
- "we have a responsibility as users of open source code to contribute back"
- internal leadship and commitment is so important.
    - People need to be recognized for the hard work they do
    - if nobody cares about open source, people will stop doing it
- "robust documentation is the difference between tools that no one will use and building things that will become central to your teammates' workflows"
- "if you can't write a 2-sentence description of what your package does, its purpose probably isn't cohesive enough"
- love that she made a video people could go back to later. This is a phenomenal way to do a walkthrough
- once you've locked things down in this package structure, you've now made it manageable for users to go in and recommend (and even fix!) improvements
- people will do things that are recognized and supported...
    + if you give developers positive feedback in their reviews and say "we love how when you find a problem you just fix it with a PR" you will find people submitting PRs!
- in Q&A:
    + Q: "How do you handle improving a thing while it's actively in use"
    + A: Stephanie gave a great description for this beginner on how to use feature branches, how to handle releases
- "try stuff, go break things and see how it goes"

**F. Deploying Tensorflow models with Sagemaker**

- Chris Fregly, Pipeline AI
- serving-time hyper params can also be tuned
- R, Python, Matlab, were made for batch. They're not runtimes that are made to run in prod
- PipelineAI tries to expose performance characteristics like scoring time, computational complexit
- other cool shit you can do:
    + cloud-level failover
    + multi-arm bandit
    + A/B testing
- with pipelineAI you can generate hardware-specific pipeline optimizations
- scikit `partial_fit`
    + http://scikit-learn.org/stable/modules/scaling_strategies.html
    + scikit thing for online training
- pipelineAI quickstart --> https://github.com/PipelineAI/pipeline/tree/master/docs/quickstart/
- "I created pipelineAI once docker started being supported on people's laptops"
- another mention of "Machine Learning the High Interest Credit Card of Technical Debt"
- `NoFlaskApp.com` now redirects to pipelineAI
    + serving a model with flask gives you a false sense of your model now being "in production"
- "Internal AI platforms are too custom to open source"
- on the order of 100s of training jobs per day, but millions of predictions per second
- AWS Sagemaker
    + released November 2017
    + custom docker images for training/serving
    + distributed tensorflow training through Estimator API
    + traffic splitting for A/B model testing
- Google Cloud ML Engine
    + mostly command-line based
    + driving tensorflow open source API
- NVIDIA will do "all these crazy tricks on your model that only people from NVIDIA know"
- TPU only recognizes google storage (not even local FS)
- for a particular type of model, they will show:
    + which cloud to use
    + what type of network
    + cost per prediction
- If I was talking to a VC, I'd be like "oh yeah well we hold out some stuff as proprietary"
    + "but between me and you guys, you can pretty much do everything"
- told a story about getting stuck in an Uber test cell
    + he couldn't get an UberX
    + saw that the guy next to him was able to
    + figured he was part of some A/B experiment
- monitoring:
    + CPU = `top`
    + GPU = `nvidia-smi`
- Istio + Chaos Monkey = Latency Monkey
- "running joke at Netflix that we were all part of Chaos Monkey. Because every few weeks someone would randomly disappear"
- the more you can reduce precision and still tolerate it, the better performance you can get on the hardware side
    + you need to decide what's acceptable statistically
- `numba` --> drop in replacement for numpy
- `tensorflow.js` --> tensforflow at the edge
    + train in your browser
    + "pathway to privacy-friendly, decentralized AI"
- Tensorflow can now talk to Kafka like any other data source (whoa)

## Day 2

**A. Realizing Explainable**

- speaker: Josh Bongard, complexity professor at U of Vermont
- fastsr aims at providing the most simple, powerful models possible by optimizing not only for error but also for model complexity.
- this is kind of like LASSO and other penalized methods
- https://github.com/cfusting/fast-symbolic-regression
- You can fit models which are semantically the same but structurally more / less complex
- Genetic programming:
    + basically sample with replacement from `operators` and `features`
- in all evolutionary algorithms, we're creating many random models
    - calculate training error for each
    - models that have high error get killed
    - then we make new randomly-modified copies based on the ones that survived
- How to do random modifications:
    + choose a node at random from the AST of one of the survivors
    + choose something at random from the bag of features or operators and replace that one node
    + "just like in biology, in some rare cases these mutations will improve your fit"
- multi-objective optimization frameworks
- we're going to determine survival based on:
    + training error
    + size
    + complexity
- Reimagine a coordinate space where X = size, Y = training error
    - Now you can try to optimize for a tradeoff between those two
    - go through and delete the totally dominated solutions
    - then, once you only have non-dominated solutions, and you make more solutions
    - "the theoretical optimum is a model with 0 features and 0 error"
- new models will tend to have worse models
    + younger models will tend to be killed off by older models
    + so you may want to only do the killing-off-models shit within certain age classes
- age-fitness pareto optimization
- objectives:
    + training error
    + age
    + size (number of features)
    + order of most nonlinear term
- "collapse of the front"...you eventually hit a point where evolution cannot find a dominated solution to kill off
- mixing and matching lasso, DTs
- GP-tree = "decision tree with genetic programming"

**B. Finding Intricate Discoveries**

- "why are hospital readmission rates so large?"
- "combining misaligned data sets"
    + like what if you are trying to combine economic, weather, and business data
- predictive modeling:
    + learn function f based on training data
    + use f to generalize to new data
- simple idea: algorithm is irrelevant if you're missing key information
- prediction can be degraded by:
    + absence of knowledge or reporting of all true X that describe Y
    + data combined from different sources may have inconsistent conditions, time periods, or matching on units
- "simple explicit model"
- paper the talk references: http://circoutcomes.ahajournals.org/content/11/Suppl_1/A118

**C. Bayesian Hieratical Model for Predictive Analytic (sic)**

- speaker: Amir Meimand
- if I tell you the price of gas in Austin, TX and Los Angeles AND NOTHING ELSE, what is your best guess for the price of gass in San Antonio, TX?
    + the price in Austin
- intutition for bayesian shit is that you have prior assumptions then update them given more data

**D. Recommendations from Henosis**

- came into this talk late
- you probably want to do more t han just give the most-likely class for a categorical recommendation problem
- function tagging
    + near-full customizability of data sources, data cleaning procedures, and variable generation
    + you build an association between functions and models


**E. JuliaDB + OnlineStats**

- speaker: Josh Day
- https://github.com/joshday/Talks/tree/master/ODSC2018_JuliaDB_OnlineStats
- "Julia works because we built it from the ground up"
- we have:
    + meta-programming
    + JIT compilation for fast for loops
- parallelism is built into the language
- really expressive type system
- consistent but not super fast growth
- juliaDB is a "distributed analytical database implemented in 100% Julia"
    + store any data type
    + turn on parallel computing with a flip of a switch
    + run on larger-than-memory dataset
- "we can get good gains from writing your analytics stuff in the same language your DB is in"
    + the pitch is basically "everything is julia"
- `NDSparse` data structure mimics a sparse array
    + if you index into a table, it's accessing them by row
    + if you index into an NDSparse object, it will take advantage of indexes
    + use this for data that is sparse over some domain
- you have to write different `get()` code based on knowledge of your data being an `NDSparse` thing or a regular table
- plotting a summary of a large dataset:
    + `Partition` and `IndexedPartition`
    + your brain can't comprehend a million points, but you could use index stats (on the indexes the DB already knows about) as the plotting inputs
- JuliaBox.com to run julia in your browser


**Tech**

- PyMC3
- Microsoft CNTK
- AllegroGraph
- Neon (deep learning)
- Apache Mahout
- Apache Ignite
- Chainer (https://chainer.org/)
- Decision Forests & "Instance-level feature importance"
- RISE labs:
    + Ray + Plasma
    + Clipper
    + Alegro
    + Arx
- meta-learning
- multi-argmed bandit
- Onnyx
- scikit `partial_fit`
