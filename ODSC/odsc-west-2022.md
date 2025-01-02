# ODSC West 2022

Nov 1-3
Virtual

## Day 1

**A. Real-time Analytics, AI & Apps with Deephaven Data Labs**

- speaker: Pete Goddard, CEO, Deephaven Data Labs
- this was a pre-recorded talk (I think)
- Deephaven projects:
    - barrage (https://github.com/deephaven/barrage)
    - "streaming tables"
- they have a "streaming table" Jupyter notebook widget which is kind of cute?
- "let's go to a real-world use-case"
    - jk jk, it's the twitter API
- "let's look at some real data now for real"
    - .... "crypto data from Coinbase"
- the audio quality was brutal, I had to get out of this after about 15 minutes
- it's pretty cool though that it can populate a streaming table over a websocket!

**B. Unifying ML with One Line of Code**

- speaker: Daniel Lenton, CEO, Ivy
- ivy supports transipiling between different frameworks
- Ivy is a transpiler and a fully-fledged ML framework
- Ivy "only wraps the functional interface of the frameworks, not the high-level classes"
- `pytorch` has "fully asynchronous execution on the GPU" and "very Pythonic interface"
- "we are adhering to the array API standard"
- `keras` is deprecated "as a unifying engine"
- neural network exchange formats
    - ONNX
    - NNEF
    - SwiftML
- ML compilers
- vendor-specific compilers
    - ICC, ICX, NVCC
- amazing talk
- "pytorch leverages dynamic control flow"
    - ivy only works for static graphs
- transpilation can be done lazily (just-in-time) or eagerly

```python
"""
transpile ENTIRE LIBRARIES
"""

import ivy
import cv2
import kornia
import tensorflow as tf

# this just "primes" ivy to transpile what it needs as things are imported
kornia = ivy.transpile(kornia, to="tensorflow")
```

- they also do module-to-module transpilation
- adding new frameworks to Ivy is easy, including ones not yet invented
- the backend can use any language: C, C++, CUDA, TorchScript
- "Just implement ~100 core functions"
    - for a framework or hardware creator to tie into Ivy
- unlocks Ivy's libraries, layers, loaders  optimizers to the new framework instantly

**C. Data Science Platforms Are Bad**

- speaker: Hugo Shi, Saturn Cloud
- most data scientists:
    - primarily working on local machines
    - running on manually-provisioned remote servers
    - have adopted (or built) a data science platform
- the bad: many platforms change how you work
    - force Python code to be packaged in highly specific ways
    - limit you to only Python
    - limit which IDEs you can use
    - often these limitations DISCOURAGE better tested, higher-quality software
- the bad: too much emphasis on notebooks
    - if all your code is in notebooks - how do you unit test it?
- "I'm not saying you shouldn't use a vendor...I am a vendor"
- "code running in Saturn Cloud is completely portable"
    - you only need Saturn Cloud APIs to orchestrate Saturn itself
    - Saturn Cloud dask clusters can easily be replaced with other clusters you choose
    - "we're planning on adding Ray clusters...they'll be the same"

**D. Turbo Boost Workflows for AI, ML, DevOps and EDA with Modern File Utilities**

- speaker: Keshav Attrey, Product Manager @ Pure Storage
- RapidFile Toolkit
    - this, I think? https://support.purestorage.com/Solutions/Linux/Linux_Reference/RapidFileToolkit
    - this is proprietary software you have to get a copy of
- uhhhhhhh the demo was literally a 4-minute recorded video????
- trash

**E. Full-Stack Machine Learning for Data Scientists**

- speaker: Hugo Bowne-Anderson
- I wasn't able to log into this one

**F. Inclusive Search and Recommendations**

- speaker: Nadia Fawaz, Senior Staff Applied Research Scientist and the Technical Lead for Inclusive AI @ Pinterest

## Day 2

**A. Responsible AI a Global Imperative for Governments and Business – Now and the Future**

- speaker: Kay Firth-Butterfield , Head of AI & Machine Learning | Member, Executive Committee | World Economic Forum
- "if we have the power to ask whales to do something, should we use that?"
    - e.g., is it ethical to induce whales to dive when a ship is coming? or should we just tell ships not to go in certain places
- is something that's 95% accurate enough if it's a surveillance tool used by a government?
- what about lethal autonomous weapons?
    - there is a U.N. working group on this
- World Economic Forum has a "smart toys rules"
    - https://www.weforum.org/agenda/2021/05/how-7-smart-toys-are-protecting-kids-data-and-safety/

**B. Unlocking High Quality Data with Ground Control**

- speaker: Lucas Chatham , Product Manager | iMerit Technology
- clean "annotated data" requires "clear guidelines for what good looks like"
- iMerit is selling a hand-labelling tool
- they deploy as a chrome extension that runs on "annotators'" local browsers
- all kinds of surveillance shit to see how "annotators" (humans hand-labelling) spent their time in the app :grimacing:
- this talk was just a product manager showing demo screens
- not a good talk

**C. Open-source Data Curation and Governance for Large and Growing Data Lakes**

- spaker: Roger Dev , Senior Architect  | LexisNexis Risk Solutions
- the remedy for complexity in curation:
    - curation organizes and showcases important aspects of the data lake
    - governance puts automated safeguards around the evolution of the data lake
- Tombolo
    - comes with a "documentation compiler"

**D. Impact of Data Science on Social Media data**

- speaker: Jyotika Singh , Director of Data Science | Placemakr
- this webinar didn't work

**E. AI Total Cost of Ownership (TCO)**

- speaker: some sales schmo from Pure Storage
- this turned into a sales pitch trying to sell you....hard drives?
    - "FlashBlade"
    - "All QLC Flash"
- this talk was basically like "we have storage, and you might store stuff when you do MACHINE LEARNING IN THE CLOUD"

## Day 3

**A. Is My NLP Model Working? The answer is harder than you think?**

- speaker: Graham Neubig, associate professor, Carnegie Mellon NeuLab
- "text generation through LMs + Prompting"
- BLEU/ROUGE Score
- github.com/Tiiiger/bert_score
    - "Embedding-based Evaluation"
    - you basically can score how close an output is to a human-provided "best" answer by taking cosine similarity between terms in embeddings
- generative text evaluation
    - github.com/neulab/BARTscore
    - P(source | hypothesis)
    - P(reference | hypothesis)
    - P(hypothesis | source)
- "learned methods" are easier to apply because they don't require "grammar engineering"
- token-based aggregate analysis
    - some systems might be better or worse based on token length!
- `explainboard_client`
- evaluation is an "arms race between generation, evaluation, and human standards"
    - better evaluation drives innovation in generation, which requires improvements in evaluation

**B. Vector Search - A gentle introduction**

- speaker: Zain Hasan, Senior Dev Advocate, SeMI Technologies
- "it is difficult to process, understand, and search through unstructured data"
- "it is difficult to use machine learning models in a scalable and secure way"
- what is a vector database?
    - stores data objects (e.g. images) and vector embeddings
    - it has to take a query, project it into this vector space, and then find the "closest" vectors
- steps:
    1. vector and index the input data (using ML)
    2. vectorize the search query (using ML)
    3. retrieve nearest-neighbors (the literal data objects, e.g. images or websites)
- vector database - weaviate
- "area of influence"
- so basically vector search is like taking input (text, images, whatever), using some model to project them into "vector space", using that same model to project queries to your search engine into "vector space", and then using similarity between the vectors to find results that are "similar" in some way to the query

**C. CI/CD for Machine Learning with CML**

- speaker: Alex Kim, solutions engineer @ Iterative
- ML workflows shouldn't be that different from software engineering
    - git repo is source of truth
    - git branches for experiments
    - automated reporting
    - pull requests, code reviews
- CML
    - command line tool for CI/CD for machine learning projects
- CML kicks off a model training running in a cloud runner, then posts back a comment with a report
- merging the PR deploys the model
- see gitlab.com/alex000kim/cml-cloud-case for an example
    - it's cool that you format what ends up in the GitHub format but just `cat`-ing stuff to a markdown file
- the recommendation for setting up creds was "set environment variables with like `AWS_ACCESS_KEY_ID` and `AWS_SECRET_KEY` in GitLab/GitHub variables" :grimacing:
- once you have this all running through your CI system, you can do other cool stuff like "trigger re-training when your underlying data changes"
    - see "CML with DVC" on the CML site
- oh this is the same company that makes DVC!
- TPI = terraform-provider-iterative
- CML can run on spot prices, and you can set a maximum spot price
- CMLD can integrate with papermill as a tool for running notebooks

**D. Cybsersecurity and Policing in the Metaverse**

- speaker: Jack McCauley, founder, Oculus VR
    - inventor of Scrolling Mouse
    - Advisor
- he was the chief engineer of Guitar Hero
- "one of the problems in the metaverse is online bullying"
    - people in the metaverse, because they can hide behind an avatar, are "making comments you'd never make to someone you met in the street"
- one of the criticisms of Second Life is that it's "not a goal-oriented piece of software"
    - said that the failure of Second Life is a warning shot to the Metaverse
- "Facebook is an advertising company with a frontend that looks a little like a social network"
    - "Facebook would have been better off just buying a video game studio than trying to create one"
- Kali Linux is the tool that can hack the Metaverse
- Vestibular illness
    - when Oculus first rolled out, 10% of people got sick or dizzy
- WPA2 is "completely vulnerable" to cyber attacks
- 5G mobile is vulnerable "at the twoer" to data and content theft
- this guy is amazing: https://en.wikipedia.org/wiki/Jack_McCauley

## Things to Google

- ANN (approximate nearest neighbors)
- autoencoder models
- BLEU/ROUGE Score (NLP metric)
- Chainer
- CML
- Dex (neural nets)
- EagerPy
- Gelu activation function
- Hierarchical Navigable Small World (HNSW, https://arxiv.org/abs/1603.09320)
- ivy (ML transpiler)
- JAX
- kornia (computer vision, built on pytorch)
- MXNEt
- neuropod
- RapidFile Toolkit
- Tombolo
- WPA2/WPA3 (wifi)
- XLA compiler
