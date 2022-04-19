# apply() meetup 2022

Date: Feb 2022
Link: https://www.applyconf.com/apply-meetup-february-2022/#agenda

## A. Model Calibration in the Etsy Ads Marketplace

* speaker: Etys people (Erica Green?)
* introduced a concept of "predicted click-through-rate" (pCTR)
* oh hey they're using LightGBM
    - jk, they wanted to move away from LightGBM (didn't say why exactly)
* "calibration" is about fitting the output predictions from a model to a known distribution
    - doesn't affect the ordering of predictions, important in this case since they're using it for a ranking task
    - "empirical distribution is very stable day-to-day"
    - fitting to a known distribution means you can interpret model predictions as probabilities
* "Platt scaling" = a parametric alternative to the sigmoid function
* can create a "reliability diagram" by plotting the average predictions against the average labels
    - x axis = predicted probability
    - y axis = observed probability

## B. What Data Engineers should know about real-time analytics

* speaker: CTO and co-founder of Rockset
    - founding engineer of RocksDB (from Facebook)
    - founding engineer of Hadoop FS (from Yahoo)
* "when I was at Facebook, I saw the photo-sharing system explode on Halloween day"
* how Amazon handles bursty traffic:
    - autoscaling
    - disaggregated architecture = "scale up and down resources independently to support bursts in data and queries"
    - disaggregation as "removing compute contention"
* aggregator-leaf-tailer architecture
    - totally segregate writes from reads
* SQL is hugely popular
* rockset: automatic "smart schemas" on ingestion
* databases
    - Postgres = have to use `ALTER TABLE` to alter schemas
    - CockroachDB = only one schema at a time

## C. Hamilton: a micro framework for creating dataframes, and its application at Stitch Fix

* generates a DAG to create a data frame, to make it easier to test, maintain, and scale feature engineering (read: pandas) code
* benefits:
    - central "feature definition store"
    - lower maintenance burden
    - allows reusability of features
* you can publish your Hamilton functions in a package
* key concept: output immutability
    - don't mutate a pandas series in place, create a new one instead
    - test this in unit tests

## D. Data engineering isn't like other types of software engineering

* speaker: Erik Bernhardsson @ Modal
    - spent 7 years at Spotify, open source Luigi
    - built the first version of SPotify's music recommender
* some ideas are still controversial
    - monorepo vs. lots of repos
    - microservices vs monolith
    - continuous deployment

## E. Data Transfer Challenges in Evaluating MLOps Platforms

* speaker: Pardis Noorzad
* ideas:
    - avoid data transfer
    - data transfer is the norm
* "SFTP is not the right solution for the cloud"

## F. The Data Engineering Lifecycle

* Joe Reis, Ternary Data
* "transformation provides the ROI for data"
* 

## To Google

* aggregator-leaf-tailer architecture (ALT)
* Hamilton (stitch fix)
* Pinot
* Platt scaling
* Redis on Flash
* Redis stream
* reliability diagram
* weight decay
