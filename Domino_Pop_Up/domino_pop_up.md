

# November 13, 2017

"Domino Data Science Pop-Up"


**A. Data Viz Stuff**

- Greg Brunner, Esri
- WebGL powering map rendering
- "is cartography becoming data science"
- github.com/maplabs/mapstyler
- a big change in the last few years....your basemap is now configurable and style-able (not a static image)
- hexbins instead of points to get you closer to something you can take action on
- ArcGIS website has a gallery of public "story maps"
- "index 3D scene layer"
    + http://www.opengeospatial.org/standard/i3s
- a proposed architecture for serving complex geospatial viz:
    + storing shapefiles in Elasticsearch
    + run batch jobs in Spark

**B. Reproducible Dashboards**

- Marc Rogers
- being acreful about terms... repeatable vs. replicable vs. reproducible
- magic commands in jupyter:
    + `%lsmagic`
    + you can pass data from Py session to R using something like `%%R -i <object_name_in_Python_scope>`

**C. Better data through data science**

- this talk is about cleaning up human-created labels
- speaker: Derrick Higgins, AmFam
- "item response theory"
    - every question on a test gives you some noisy piece of information about a latent attribute
- MACE (multi-annotator something something):
    + https://www.isi.edu/publications/licensed-sw/mace/

**D. City of Chicago, West Nile**

- speakers:
    + Nick Lucious
    + Gene Leynes
- city of chicago approahces to preventing west nile virus:
    + larvicide in stormwater drains
    + DNA tests of mosquitoes
    + spraying stuff when WNV is present
- city of chicago "open data portal"
- "old-fashioned confusion matrix"
- water sensors feeding the E Coli model:
    + weather sensors
    + water sensors (measuring cloudiness, wave height)
- one ooff datasets:
    + when sewage water was put into Lake Michigan
    + when locks open / close
- these anomalies are very difficult to predict
- chicago.github.io
- used k-means to cluster together beaches that were likely to have E. Coli
    + forthcoming paper
- city tech plan:
    + "work with civic technologies innovators to develop creative solutions to city challengers"
    + 1000+ hours dedicated to this project through Chi Hack Night
- "GitHub Punch Card" = cool
- OpenGrid --> https://github.com/Chicago/opengrid
- the shape of  the beach matters for this:
    + some beaches that hold water more will have more standing water
    + adding "culverts in the break waters" can allow some water through and maybe stop E Coli from growing
- "everything I'm writing is just R and cron jobs"

**E. What's in Your Workflow?**

- Emily Riedere, Capital One
- reproducibility as a "brand"
- sister orgs:
    + data carpentry
    + software carpentry
- out business analysts had to admit that "their problem is not so special, or so unique, that it cannot be abstracted into a package"
- TL;DR they created an internal R package for cash flow analysis then helped analysts transition to it
    + now working on training people up, internal community building
- called their internal package `tidyCF` ("tidy cash flow")

**F. Cars.com stuff**

- speaker: Addhyan Pandey, Lead data scientist
- DS tasks at Cars.com:
    + guaranteeing relevant but diverse set of cars
- trying to cut down the big block of text in results:
    + put descriptions into vector space to help identify duplicate vehicles
-


## Things to Google

- webGL
- RSTAN
- pySTAN
