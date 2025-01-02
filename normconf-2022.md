# normConf 2022

## A. How small can I get that Docker container?

* speaker: Matthijs Brouns
* don't ignore .dockerignore
* use a small base image
* use as few layers as possible
* remove build-time dependencies

## B. Spark horror stories from the field

* speaker: Guenia Izquierdo
* each Spark executor has a "slot" that can be filled with a task
* for better testing: modularize into more utility functions
* Spark breaks your stuff into multiple jobs, and each job is divided into multiple stages, which are then broken to tasks
    - each "task" works on one core and on one partition of data
* remove all displays and prints that trigger an action
* "you rarely ever need to iterate over a data frame"
* sending all records to the driver defeats the purpose of having a parallel system
    * don't `.collect()` until AFTER grouping and filtering
* wherever possible, use Spark native functions instead of UDFs
    - Spark's main stuff is compact and optimized for Spark
    - writing your own code, it has to be serialized, sent to executors, then deserialized
    - Spark cannot optimize through your custom code

## C. Geriatric data science: life after senior

* speaker: Luca Belli
* "any sufficiently advanced engineer is indistinguishable from management"
* "the technical work is the easy part"

## D. A Game of Construction

* speaker: Helena Sarin
* art-making "it is all a game of construction"
* uses intermediate outputs, checkpoints from GANs to generate art
* "neural bricolage manifesto"
* "the book of veGAN" - Kate Kay
* potteryGan = "generative pottery"
* she was in the first cohort of the fastAI course
    - and read the Keras book from Francois Chollet
* basically this talk was like "I use GANs to make art"

## E. Hack your way to a better API

* speaker: Zachary Blackwood
* "I want to convince you that the internals of the software you're using is more accessible than you think"
* messing around:
    - monkey patching
    - spelunking: "command-click in pycharm"
* VS Code is all Electron apps these days
* "everything is a website now, what does open developer tools get me"

## F. What's the simplest possible thing that might work, and why didn't you try that first?

* speaker: Joel Grus
* for text classification, just use BERT
* Ayn Rand: "contradictions do not exist. When you think you have one, check your premises. One of them is wrong"
* a tool is "simple" if it's "simple to use correctly"
* as our tools get better, the boundary between simple and complex changes
* "manifest plainness, reduce selfishness, have few desires, emrace simplicity"
* "regularization is more complex as a process, but will produce a simpler model"

## G. It's all about cost: how to think about machine learning products

* speaker: Peter Sobot
* Canadian engineers - Iron ring
* functional requirements = "how we know if we're done"
* non-functional requirements = "how we know how well we did"

## H. ML Doesn't always replace rules, sometimes they work together

* speaker: Jeremy Jordan
* a system of rules is harded to maintain than a machine learning system

## I. All my machine learning problems are actually data management problems

* speaker: Shreya
* "I want to show you a new way to diagnose ML bugs, and spoiler it involved materialized views"
* ML Pipeline DAGs suck because:
    - they rely on low-level task scheduling
* "Inconsistent MV Policies in ML Pipelines" (Hermann, 2017)

## J. Three cheers for OpenAPI 3

* speaker: Jowanza Joseph
* OpenAPI 3 is a spec for describing services
* there is an OpenAPI "listener" that will try to create a spec out of listening to curl requests
* "if you've used Flask or Django, you used OpenAPI"

## K. Ethan Rosenthal and the M1 misadventure

* speaker: Ethan Rosenthal
* "if you want to deal with different versions of python, use `pyenv`"
* had a bunch of questionable advice like:
    - use poetry
    - use pyenv
* made a really good point though, "seeing a leak in the abstractions makes you doubt yourself"

## L. Data is the new coffee

* speaker: peter baumgartner
* "inter-rater reliability" or "inter-annotator agreement"
* agreement metrics help you understand how reliable human annotations are
    - if humans can't even agree on the labels, how could a model learn?

## M. How to Translate to PM Speak and Back

* speaker: Katie Bauer
* "once broke prod by pushing something that contained too many emojis"
* after she started seeing that her relationship was becoming antagonistic, learned "assume good intent"
* PMs are always asking causal questions
    - they're interested in finding out what buttons they can push, and what happens when they do that
    - so focus your work on things they can control
    - prioritize logical consistency over being technically correct
    - describe your results as inputs and outputs
* accept that no translation will be perfect
    - there is no direct PM equivalent for "statistical significance"
    - pick your battles on when exact translations matters
* I think this was my favorite talk of the conference
* "data scientists should not report into marketing"

## N. Tracer bullets and working backwards: simple framework for solving problems

* speaker: Caitlin Hudon
* tracer bullet = "get through each layer of logic as fast as possible"
* books:
    - "Thinkings in Beta"
    - "The Pragmatic Programmer"

## O. When not to use SQL

* speaker: Sean J Taylor
* "don't re-invent nouns, re-invent verbs"

## P. Building an HTTPS Model API for Cheap

* speaker: Ben Labaschin
* AWS, Docker, and the NormConf API
* your tools should make your job easier...time is expensive
* "first a program should do the thing, but lord almighty wouldn't it be nice if I didn't have to learn how to use them"

## Q. Data's desire paths: shortcuts and lessons from industrial recommender systems

* speaker: James Kirk
* most recommender projects are poorly framed
* a good recommender has:
    - a clearly-defined user
    - a measurable definition of success
    - a clear relationship between recommender success and business success
    - data and a tech stack ready to implement and iterate on recommendations
* "offline NDCG" metric
* plot an offline metric against some other online metric
    - like even if they aren't the same
    - then you can find some relationship between training-side improvements and the real-world performance of your model/product
* "don't be afraid to pre-calculate"
    - especially for recommenders! They did this at Spotify and it was fine.
    - keep serving the simple stuff for as long as you can
* recommender systems are "about, by, and for people"
*

# Things to Google

* BERT
* Ganglia (Spark monitoring)
* "Inconsistent MV Policies in ML Pipelines" (Hermann, 2017)
* Keras book (chollet)
* Malloy
* prodigy (annotation tool)
* PRQL
* spaCy
