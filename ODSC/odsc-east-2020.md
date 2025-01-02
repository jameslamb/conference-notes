

# Day 1

## A. Enhancing Browsing Experiences

* speaker: Zona Kostic, PhD
* "smart" = an ML backend, an application interface
* data visualization as a tool to build trust from humans
* "I'm using visualization as a mediator"
* GANpaint --> interactively edit a picture  with GANs
    - http://ganpaint.io/
* "browsing" is like "looking around without an exact gooal in mind"
    - that is a different experience than search, where you have a specific goal in mind
* Codex Atlanticus
    - https://www.codex-atlanticus.it/
* "unlike simple charts, it hasn't been widely determined what peoople can perceive from 'glanceable visualization' during short  perioods of time and limit display"

## B. Continuous Learning Systems: Building ML Systems That Learn from Their Mistakes

* speaker: Anuj Gupta, header of ML at Vahan
* you have to look for drift in model results AND drift in input data
    * drift in input data might be looked at moore directly by plotting summary statistics of each feature over time
        - changes can tell you if you are getting out of sample
* responses to feature drift in this example:
    - need to build a per-brand model to get more specific
    - learn from mistakes by looking at which messages got respoonses
* if feedback is  utilized well:
    - you adapt to changes in features, either by changing the features to something less likely to change or just by retraining now that you have more sample space
* two ways to adapt:
    - collect datta and do periodic re-training
    - online, continuous learning

## C. The Future of MLOps and How We got here

* company: `dotscience`
    - https://dotscience.com/
* they literally have a "deploy" button
    - that will create a new deployment in Kubernetes, and they give you a Grafana dashboard for it out of the box
    - of COURSE  the moodel they came up with is a computer vision "is this a stop sign" type model
    - they made a little predictor where you click "predict" to send an image file
    -

    ticket for Amazon equipment: 0311490290

## D. How to Solve Real-World Computer Vision Problems Using Open-Source

* `microsoft/computervision-recipes`
* "now, rather than designing features we learn them"
    - contrasting deep learning to the "old" way of manually creating features and feeding to traditional approoaches like tree-based models
* "triplet loss learning"
* object detection
    * R-CNN
    * Fast R-CNN
    * Faster R-CNN
    * Mask R-CNN
* approach with R-CNN
    * you extract "region proposals" from an image, then feed each "region propoosal" into a CNN
    * each regioon is classified as "car", "horse", "etc."
* most state-of-the-art computer vision is based on DNNs
* start with a DNN pre-trained on ImageNet, then fine-tune on small numbers of images
* you can create custom code with PyTorch but it requires a lot of knowledge

## E. Actionable Ethics for Data Scientists

* Emily Miller, DrivenData
* good intentions are not enough
* data collection:
    - informed consent
    - collection bias
    - limit PII exposure
* data storage
    - data security
    - right to be forgotten
    - data retention plan
* analysis
    - missing perspectives
    - honest representation
    - privacy in analysis
    - auditability
    - you shouldn't ask "is my dataset biased" but "how is my dataset biased"
* strava example:
    - Strava app outlined where secret military bases were
    - https://www.theguardian.com/world/2018/jan/28/fitness-tracking-app-gives-away-location-of-secret-us-army-bases
*
