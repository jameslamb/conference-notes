# Berkeley Data Dialogs (11/6/2016)

**A. Data Haves and Have-Notes**

- speaker: Edd Wilder-James
- role: founding chair of Strata
- 80% of the work will always be data prep
	- your competitive advantage is digging deeper into the data
- why is data the most valuable thing?
- "up until about five years ago, IT was just faster paper"
- "it's much easier for a company that knows data to move into an industry than for an incumbent in that industry to become data-driven"
	- a culture of data is hard to retrofit
- data driven companies create "reinforcing ecosystems"
	- e.g. Google Maps is fun to use + the more you use it the better it gets
- shaping forces:
	- fungibility of software, hardware, network
	- big data is a macro-microscope
	- probabilistic is often good enough
- a key recommendation: "instrument what you do"
- "design in data acquisition"
- lots of companies in the space of: "we want to be data-driven but we don't know how"
- building for experiments:
	- make it cheap
	- make it quick
	- don't break things
		- APIs, platforms, simulation
		- make operations a platform for innovation
- get data infrastructure right early
	- make careful choices about what data you'll collect
	- get business involved from the beginning

**B. Using Machine Learning for Predicting NFL games**

- baseline = vegas point spreads
- used labeled training data + supervised learning
- outcome: 0/1 did the teamp we expected to win win?
- you can explore machine learning with just doing fun stuff!
- presenter: amitb@ischool.berkeley.edu

**C. Data Science in Healthcare**

- issues for employers:
	- self-insured empoyers directly pay most of the cost
	- few options to control this cose
	- employees underutilize related benefits
- bigger companies are "self-insured"
	- Employers as insurance providers
	- employers end up paying out on claims
- you generally only know the price of your healthcare after the service is rendered
	- and the out-of-pocket pricing is very complicated
- Castlight platform:
	- empower customers' empoees and their families to make better healthcare decisions
	- find best care based on cost, quality, and convenience
- Castlight dataset:
	- very large database of cross-payer claims across entire US
	- consolidated quality data
	- application engagement data:
		- searches
		- provider views, care team creation, and reviews
- predicting prices of medical/health services
- **Cost and quality in U.S. healthcare**
	- it's an opaque, non-transparent market
- why is transparency important?
	- reduce fear and uncertainty that may lead people to:
		- neglect needed (preventative) care
		- choose unqisely, such as avoidable visits to an ER
	- reduce unjustifiably wide variance and overall level of prices
- problem: "there are providers for whom we want to predict prices, but we have no claims"
- you can predict quantiles with "qualit regression forest" technique
- Castlight floats recommendations like:
	- where should I get this type of care?
	- what are my self-care options?
- **KEY FOR UPTAKE:** "You get really good engagement from people when you give them targeted, short information that is relevant to them"

**D. Agriculture: the next machine learning frontier**

- speaker: Sivan Aldor-Noiman
- firm: The Climate Corporation
- statistics basically started in agriculture
- agriculture:
	- rising population
	- rising animal protein consumption
	- declining arable land
- getting the data can be as hard as doing something useful w/ it
- "clients will not trust us if we build black boxes"
	- going into industries and telling someone you can do their thing better than them isn't a good strategy
- "I've always been promised the ultimate dataset, and I haven't been given it yet"
- struggles in learning features:
	- inherent complexity
	- latent features
	- curse of dimensionality
	- multi-task learning
- heterogeneous sources: consider "sensor fusion"
- Bayesian approach: learn from data + experts' opinions
- a key: **build products that teach your users about data science**

**E. Predicting Breast Cancer Proliferation Scores with Apache SystemML**

- speakers: Mike Dusenberry, Madison J Myers
- firm: IBM Spark Technology Center
- paper: "automated grading of gliomas using Deep Learning in Digital Pathology Images"
- convolutional neural nets (CNNs) as useful tool for this type of task
- idea:
	- if the whole tumor is given the whole grade....you can split up the image into sub-images and suddely your dataset is bigger!
- their process was basically:
	1. take 500 images
	2. break into millions of sub-images
- what is Spark?
	- distributed and fast engine for large-scale data processing
	- combines ML, SQL, streaming
	- extends Scala idioms, as well as R/Python DataFrame idioms
- what is Apache SystemML?
	- machine learning sysem for running distributed linear algebra on top of Apache Spark
	- exposes high-level R-like and Python-like languages focused on linear algebra
	- APIs for Python, Scala, Spark
- takeaways:
	- Nice case study for a small-scale use case to a bigger validation study
	- if youn understand your data and the assumptions behind it, you can create a more tractable ML problem

**F. Data Viz and Design Thinking**

- speaker: Zachary Sam Zaiss (@zszaiss)
- firm: Microsoft
- toolbar redux in Visual Studio 2010
	- a tool for authoring code
- key takeaway: seek out your UX counterparts
- DS communicates in attributes, models....UX researchers communicate in stories, scenarios
- tip 2: "partner on the data"
- areas for connecting on uncertainty:
	- disclose and discuss assumption, and cultivate a data culture of transparency around them
	- explore the context of outliers vis-a-vis experience attributes
	- check for treatment effects with critical A|B test
- "not all outliers are interesting"

**G. Trust and the Sharing Economy**

- speaker: Paolo Parigi
- firm: Uber
- in sharing economy platforms, users interaction and build relationships
- weaker ties between users as a measure of trust in the platform
- consider interpersonal trust vs. trust in the platform
- "distance" as measured by "number of bits you have to flip"

**H. The Big Brother You Want**

- "people largely don't care that much about data collection"
- maybe people don't care about privacy?
	- "it is easy to encrypt your email, but most people don't"
	- "it is easy to anonymize your browsing behavior" (e.g. Tor)
	- "we generally use the default, very open settings on social media"
	- "we regularly hand over plain-text copies of our credit crad information"
	- "the Patriot act was passed with almost no serious debate"
- finding --> even companies collecting large quantities of data aren't doing much with it

**I. Square Capital**

- square capital data science:
	- default, underwriting, and macroeconomic risk
	- business, operations, and marketing optimization
	- moonshot research and product development
- run all models simultaneously
- you can score people with different models to measure how bumpy the model progression has been over time
	- once you know this, you can start sunsetting models
	- and then really pick up a regular cadence of updating models and sunsetting old ones
- **Better data will always beat better models**



