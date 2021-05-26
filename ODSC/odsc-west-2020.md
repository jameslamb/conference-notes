# ODSC West

October 29-30
Virtual

## Day 1

**A. Keynote: Jeannette M Wing**

- monopsony: 1 buyer and multiple sellers
- "deconfounder": intentionally adding noise to improve model performance

**B. Keynote: Ben Taylor**

- "Our Applied AI Future"
- wild story to start:
    - living in the woods while going to school
    - talked about getting arrested
    - started learning to code because people wanted to comment on his blog, so he needed to know HTML / CSS
- this guy worked at HireVue and used machine learning to screen resumes 0_o
- "back in 2006, I was concerned with keeping my data science team happy, because if I didn't they'd get a 20% raise from a company down the street."
    - now, "play time is over"
    - "it's gone from KPIs to OKRs"
    - you can't do these research-y projects where it takes months to deliver a model

**C. Keynote: John Montgomery, Aniththa Umamahesan**

- so far, John M has just basically said "hey we're Microsoft and we have lots of GPUs"
- ok so this is just an AzureML demo
- "AutoML does what a data scientist typically does in days, but in minutes or hours"
    - gave an example of Little Caesar's using Azure AutoML
- Aniththa then did a demo of AutoML
- this talk was a useless sales demo
    - "AutoML is not a useful thing for computer vision"
    - "AutoML is an accelerant for a data scientist, not a replacement"

**D. Topic-Adjusted Visibility Metric for Scientific Aritcles**

- Tian Zheng, Columbia University
- the raw data in this study was citations
- topic-adjusted visibility:
    - accounts for field variation in citation practices
    - derives from joint modeling of:
        - text in articles
        - citations among them
- connectivity of article in citation network depends on:
    - topic compatibility of reseach fields
    - articles visibility to articles in a position to cite it
- LDA
    - uncover topics from text (bag-of-words)
    - each document exhibits K latent topics with varying proportions
    - topics are distributions over vocabulary
    - draw topic assignments for each word and the word from assigned topic
- the intuition behind Latent Dirichlet Allocation: "topics are probability distributions over vocabulary"
- MMSB
    - membership an individual can assume is random or "mixed"
    - an individual can have a "profile" of membership, a vector of probabilities

**E. Making Deep Learning Efficient**

- deep learning an deeep neural nets are "a subset of machine learning"
- why is deep learning getting better?
    - improvements in algorithms from research focus
    - data availability
    - improving hardware
- recommendation problem: 1B users, 1B products, 50 milliseconds to predict
    - you can use deep learning models training on vectors of embeddings, which are a lightweight way to predict recommended things
- DNNs for NLP
- "despite work on frameworks, doing deep learning work still requires a lot of expertise"
- scaling synchronous stochastic gradient descent
    - a bunch of research groups (Berkeley, Google, Amazon, Facebook, fast.ai, Tencent) worked hard on bringing down the time to train a ResNet50 model
- the pace of innovation in recommender systems has been much slower than computer vision
    - specifically, the "ability to bring down training time for good performance"
    - research in recommenders is a lot harder to do...it's at the core value of businesses with the best data, so they don't expose their realistic models or datasets (e.g. facebook. alibaba)
- "flat loss landscape":
    - 2-bit quantization
- to rewatch: https://register.gotowebinar.com/recording/recordingView?webinarKey=3098783717706104845&registrantEmail=jaylamb20%40gmail.com
- in deep learning, you don't have predefined features....you use layers of weights to develop feature "layers"
- SqueezeNet: trying to get the same performance gains as AlexNet, but with less parameters
- "when I think about why we've had big improvements in deep learning, I don't think of innovation in neural net architectures as a major reason"
- he thinks the hardware improvements have been the most important factor in improved performance from DL
- Deepscale - aquired by Tesla
    - "Why Tesla quietly acquired deepscale, a company specializing in 'squeezing' AI"
- ClickIt: a Chrome plugin that thinks it can identify a piece of clothing from a Youtube video
- natural language understanding: GLUE benchmark
- "deep learning is displacing other types of machine learning"...and "the primary driver is that these types of models can take good advantage of increases in computing power, ease of distributed computing"
- the approach that has been most successful for horizontally scaling deep learning is "data parallelism"
    - you replicate the entire neural net model onto each processor
    - distribute the SGD batch evenly across each processor
    - then each processor sends back the results of one iteration, and those results are blended in some way to update the global model
- recommendation systems are probably the least likely to be moved to the edge
- effective use of deep learning = EFFICIENT use of deep learning
- 

**F. Bayesian Workflow as Demonstrated with a Coronavirus Example**

- Andrew Gelman
- couldn't see him or his screen the whole talk. Tried asking the staff what was going on, they ignored me and he just kept talking. Had to leave early

**G. ML Easel - Tredence's Data Science and ML Engineering Workbench**

- Changa Reddy, Tredence Inc.
- this talk sucked. It was just recycled slides about "the machine learning lifecycle", didn't explain anything new or interesting

**H. Design Principles of Distributed Systems with Dask and PySpark**

- Holden Karau
    - many years ago I signed a deal with the devil and it's served me well, but I had to learn Java
    - I've worked on Spark for the better part of the last decade
- Matt Rocklin: we try to dispel this idea like "oh Dask is just a way to scale your numpy / Dask code"
- Holden: I just wrote a book about ML in Kubeflow
- Holden's new blog: http://scalingpythonml.com/
- Holden: "I literally woke up in the middle of the night thinking I'd misconfigured my garbage collector"
- Holden: "I wish I was better at lying, but I have a fake Russian accent when I start lying"
- some issues:
    - Dask's containers don't really work with Arm yet
        - and maybe neither is conda
    - Holden: I wanted to use pyarrow
        - Matt: good luck
    - Matt: "everybody uses cloudpickle"
        - Holden: "we have our own forked version of cloudpickle, that lives inside of Spark, that is shipped with Spark"
        - Holden: "whoever worked on that has left, and now we're in this weird state where no one understands that code and people just copy in source code from cloudpickle and mess around with it until the tests pass"
    - Matt: "it's kind of like Spark's 'driver' was broken into two pieces in Dask...'client' and 'scheduler'"
    - Matt: "we don't need anything like Livy in the Dask ecosystem"
    - Matt: "we started as a single-machine system first, distributed came later"
        - local is the thing that works, distributed was the weird thing...and it forced us to think hard about how to separate things out
        - Holden: in Spark, we made a distributed thing first and then bolted on local mode to make our tests work
    - Holden: "Spark doesn't have any tooling for managing Python environments"
    - Matt: "Spark was designed for SQL, dataframe-y things, so you could optimize at a high level. In Dask, we have much more varied workloads, so we had to do optimizations at a lower level."
    - Holden: "the fastest data to process is the data you don't have to read"
    - Matt: "a lot of Dask users are on HPC systems like SLURM, designed for batch jobs"
    - Holden: "I feel like I have to apologize for working on Spark"

**I. Learning with Limited Labels**

- "select the data close to the target"
- I got to this talk 10 minutes late and couldn't follow it because I missed the setup...so went to a different one

**J. Creating Equality and Inclusivity with Feature Engineering**

- Vida Williams
- NCBI Science Oath: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3910371/
- she was just reading stuff, it felt like. It was super boring
- "mitigating bias is situated in the wrangling of data"
- think about this....a model you train on presidential elections will always predict a white male
- "by fixing the answer, you're solving a problem that looks different"
- two types of equality:
    - equality of outcome vs. equality of opportunity

**K. Using Artificial Intelligence to Save Lives at Birth**

- Charles Onu
- the baby's cry is designed to be loud
- birth asphyxia:
    - caused by inadequate oxygen supply
    - can cause death, or long-term disabilities:
        - cerebral palsy
        - hearing loss
        - learning disability
- babies with birth asphyxia have different cries!
    - increased pitch
    - instability in fundamental frequency
    - longer pauses
- they trained a machine learning algorithm (SVM, Neural nets) to try to detect birth asphyxia based on cries
- the app: Ubenwa
    - this means "the cry of the baby" in Igbo
- clinical studies started in November 2019

## Day 2

**A. Generalized Deep Reinforcement Learning for Solving Combinatorial Optimization Problems**

- "learning-based approaches" mean that models can "gain experience" and "become experts"
- you evaluate a model with "policies"

**B. Frontiers of Proabilistic Machine Learning**

- Zoubin Ghahramani
- automatic differentiation
    - you don't have to write derivatives by hand any more, software can do it for you
- "staying close to identity helps make models deep"
    - ReLU, LSTMs, GRUs, ResNets
    - tricks with the activation functions and connectivity models lets you make deeper models
- stochastic optimization works surprisingly well
- parameter tying (like convolution) is helpful
- initialization matters a lot
- limitations of deep learning:
    - very data hungry
    - very compute-intensive
    - easily fooled by adversarial examples
    - finicky to optimise (non-convex + choice of architecture)
    - uninterpretable black-boxes, difficult to trust
    - non-trivial to incorporate prior knowledge, symbolic representations
    - poor at representing uncertainty
- uncertainty is essential for active learning, black-box optimizations, reinforcement learning, and other "exploration-exploitation tradeoffs"
- probabilistic (read: Bayesian) models are a good framework for putting prior knowledge into models
- bayesian deep learning
- data are now ubiquitous; there is great value from understanding this data, building models and making predictions
- probabilistic modelling offers a framework for building AI systems that reason in an uncertain world and learn from data

**C. The Future of Computing is Distributed**

- Ion Stoica (Databricks cofounder)
    - comes from RISE lab at Berkeley
- the first distributed system was the ARPA Network (precursor of the internet)
    - led to development of email
- 1970s: ARPA net
- 1980s: high-performance computing
- 1990s: internet, web
- 2000s: big data
- every 18 months over the last decade, the petaflops/s required to train state-of-the-art models has increased 35x
- the pace of change in moore's law is too slow to keep up with the pace of increasing demands for deep learning
- specialized hardware: these trade functionality for performance
- his pitch is "the only way to keep up with the demands of machine learning is to go distributed"
- started talking about Ray
    - described it as "universal framework for distributed computing (Python and Java)"
- key features of Ray:
    - execute funcitons as "tasks", classes as "actors"
    - asynchronous execution
    - distributed data
- components:
    - `tune`: hyperparameter tuning
    - `rllib`: reinforcement learning
    - `ray-serve`
    - `raysgd`
- `optuna`, `horovod` are using `ray`
- `spaCy` uses `ray`
- Amazon Sagemaker, Azure, use `rllib`
- Dask running on Ray is "5x faster", "more resilient and scalable"

**D. Accelerating NLP Model Training and Deployment with Pytorch**

- Prasanth Pulavarthi (Microsoft, co-founder of ONNX)
- Pytorch + Hugging Face + ONNX Runtime
    - on Azure Machine Learning
- Visual Studio used pytorch + ONNX runtime to train the GPT-2 model that is used for the Visual Studio code completion magic
- why is ONNX runtime faster?
    - static graph optimization like "constant folding", "redundant node elimination"
    - optimal gradient graph
    - memory efficiency
    - CUDA kernel optimization
        - Op fusion
        - Optimized cuDNN kernels
        - removing redundant computation
    - other training capabilities
        - AdaSum
        - DeepSpeed ZeRO
        - distributed training parallelism modes
        - mixed-precision training
- ONNX runtime knows which old memory can be reclaimed, base on the graph

**E. The State of Severless and Applications to AI**

- Joe Hellerstein, Berkeley, Trifacta
- functions-as-a-service (FaaS) as way to "program the cloud"
- three limitations of AWS Lambda
    - I/O bottlenecks
        - 10-100x higher latency than SSD disks on your laptop
    - 15-minute lifetimes
        - functionas routinely fail, can't assume any session context
        - makes stateful stuff hard
    - No inbound network communication
        - "communicate" through global services on every call
- embrace "state"
    - data gravity: expensive to move state around
    - distributed consistency: the "correctness" problem is difficult and unavoidable
- consistency is complicated:
    - consensus (paxos, etc.)
    - transaction commit
- James Hamilton (IBM, MS, Amazon):
    - "the first principle of successful scalability is to batter the consistency mechanisms down to a minimum, move them off the critical path, hide them in a rarely visited corner of the system, and then make it as hard as possible for application developers to get permission to use them"
- "tail latency" problem....there is a long tail in performance of machines. Also called the "straggler effect"
    - the bigger the system, the more likely you spend a long time you wait for one thing
    - performance is determienbd by the slowest member(s)
    - you can have a problem of cascading slowdowns
- Peter Bailis...databases don't understand application semantics
- CALM: consistency as logic monotonicity
    - Theorem: a distributed program P has a consistent, coordination-free distributed implementation if and only if it is monotonic
    - coordination means scaling something will lead to bad things
    - monotonic means
- "Keeping CALM: When Distributed Consistency is Easy"
    - https://arxiv.org/pdf/1901.01930.pdf
- shared-nothing at all scales
    - avoiding coordination is the key to scaling
- cloudburst:
    - https://github.com/hydro-project/cloudburst
    - Anna KVS: https://github.com/hydro-project/anna
- motion planning on serverless:
    - low-latency simultaneous launch of 100s of functions, with the ability for one lambda to tell all the others "hey I'm done"
- http://bloom-lang.net
- https://hydro-project.github.io
- https://bit.ly/stateofserverlessart
- amazing talk, 10/10 would recommend

**F. Continuous-time Deep Models for Forecasting Sparse Time Series**

- David Duvenaud, University of Toronto
- limitations of RNN-based models
    - not a well-defined generative model, it's only good at one-step-ahead predictions
    - no explicit use of Bayes' rule, just makes predictions
    - hidden state h represents model's belif about system's future....not the same as system state
- latent variable models:
    - Kalman filters, hidden markov models, deep markov models
    - these says "I don't observe all history, just the current state"
- ODE latent-variable model
    - quantify uncertainty about the state
- very cool talk but a little over my head, switched to a different one

**G. A Comparison of Topic Modeling Methods in Python**

- Russel Martin, Data Incubator
- eh this one was kind of boring, just a guy stepping through a notebook

**H. Just Machine Learning**

- Tina Eliassi-Rad, Northeastern University
- the term "machine learning" was coined by Arthur Sauel in 1959
    - the Samuel Checkers-playing program
- "assessing risk" and "rank" are popular tasks because machine learning people know a lot about them
- "precision parity"
    - "the probability that you have breast cancer given that my model says you do should be the same regardless of whether you are male or female"
- some issues with using ML for policy decisions
    - no uncertainty values to the human-decisionmaker
    - do not incorporate context
- "learning to place": building a classifier for pairwise preference
- Tracey Meares: in criminal justic, people care more about procedural justice than jusice in outcomes
- laws can be thought of as "constraints" and policies as "implementations of those constraints"
- if you use machine learning to examine the effects of a policy, you can try to recreate the intent of the policy
- margaret Mitchel - Model Cards
- "the undersampled majority"
- we can learn from "aspirational data" or "complex networks"
- relational dependencies....individual fairness, guilt-by-association
- datasheets for datasets by Timnit Gebru:
    - "if you're gonna release data, it should have a long-form birth certificate"
- we need to incorporate normativity ("should" questions) through the entire "well-posed learning problem"

**I. What if We Could Use Machine Learning Models as Database Tables?**

- Jorge Torres
- "traditional machine learning makes it seem like ML is another application layer"
- the model as a table is called an "AI-Table"
- github.com/mindsdb/mindsdb
- training a model is like `INSERT INTO predictors`

**J. The Bayesians Are Coming! The Bayesians are Coming, to Time Series**

- Aric LaBarr, NC State University
- omg I want to take a class from this guy, he's great
- in timeseries data, the rows are dependent on each other
- exponential smoothing = "weights should emphasize the most recent data"
- MINIC
- "multivariate regression is NOT multiple regression"
- "multiple regression" = "multiple target variables"
    - like a Vector Autoregression
- Bayesian Autoregressive (BAR) models
    - same model structure as a frequentist model
- "we use the gamma distribution for variances because it's right-tailed"
- a Bayesian model will give you a distribution of forecasts, not a single point
- why just pick one model? "I think people in timeseries sometimes forget about the power of ensembling"

**K. Diversity in Data Science: Challenges and Possibilities**

- Marie Desjardins
- 18% of data science professionals in the U.S. are female, 22% globally are female
- how computer science became so unequal:
    - "weeder" classes in compsci programs
    - non-family-friendly work environments in tech jobs and computer pioneers
    - "nerd in a cubicle" image that Dilbert and others propagated
    - "brogrammer" culture...working with computers involved dealing with people who were aggressive, boastful

## Things to Google

- [Druid](https://druid.apache.org/)
- de-confounder
- convolutions / CNN
- ONNX, ONNX Runtime
    - https://github.com/microsoft/onnxruntime
    - https://github.com/microsoft/onnxruntime-training-examples
- `DeepSpeed`
- Mixed Membership Stochastic Blockmodel
- LAMB on SQUAD
    - ["Large Batch Optimization for Deep Learning"](https://arxiv.org/pdf/1904.00962.pdf)
- 2-bit quantization
- shape of the "loss landscape"
- Q-BERT
- Hough transform
- histogram accumulation
- eigen decomposition
- feature matching
- SqueezeNet
- tensorflow-lite
- MobileBERT
- The Algorithmic Accountability Act of 2019
- graph partitioning: normalized cuts objective
- JAX
    - https://github.com/google/jax
- Bayesian neural network
- Gaussian Process Regression
- Bayesian Linear Regression
- GPflow
- turing
    - https://dl.acm.org/doi/abs/10.1145/53580.53581
- horovod
- Dask on Ray
    - https://docs.ray.io/en/master/dask-on-ray.html
- MARS (Ray)
- Hugging Face
- AdaSum
- DeepSpeed ZeRO
- cloudburst
- Anna KVS
- ODESolve, ODE latent-variable model
- poisson process likelihoods
- precision parity, true positive parity, false positive parity
    - Chouldechova (2016)
    - Kleinberg (2016)
- networks: "closing triangles"
- MINIC (`auto.arima()`)
- EACF
