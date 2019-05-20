# satRdays Chicago

April 2019

## A. Intros

- there was much applauding
- more than 0 people thought the wifi password being `GOGREEN!` was an MSU reference even though we're in a university whose colors are green and green

## B. Keynote

## C. Industry Session

### 1. "Correcting Bias in Customer Acquisition Models"

- speaker: Peter Cooman
- detecting vs. removing bias are two different activities
- speaker claimed "a simple and fast algorithm for removing bias"
    + ...in a learning-to-rank task or the form "recommend top K customers for some campaign"
- AFAICT the thing he did was intentionally resample to even out his training set based on attributes he wanted to avoid forming a bias against

### 2. "Building an Analytics Culture @ Allstate"

- speaker: Adam Austin
- "If you think insurance is boring...just don't say it in an interview"

### 3. "MoRtality: Using R for Life Insurance"

- speaker: Annie Wang
- "an actuary is someone who quantifies insurance risk"
- pharmacies sell data on what you're taking
- "John Hancock's new program offers life insurance discount if you send them your wearable data"

### 4. "Creating Fuller Maps with R: Filling in the Missing Values"

- Brett Kobold
- `sf::st_touches()`

## D. JD Long Keynote

- this dude rewrote the R Cookbook from O'Reilly
- he's an agg economist
- Kathy Sierra concepts on learning and the "suck threshold"
    + https://headrush.typepad.com/creating_passionate_users/2005/10/getting_users_p.html
- if you're trying to transfer people off of spreadsheets and into scripting languages, start by teaching them better Excel!
    + so like start with named ranges and you'll get pretty close to teaching them R / Python data frame syntax anyway!
    + and if you fail then hey at least they're better at Excel
- don't try to completely change workflows or your colleagues
    + aim for 10% better
    + "you'll find if you give people a taste, they'll go out and learn more"
    + small victories matter!

## E. Session 3

### 1. "Teaching Reproducible Spatial Analysis in R"

- speaker: Angela Li
- "R spatial adcovate"
- spatialanalysis.github.io
- `bookdown`, `blogdown` to write websites from R
- The `R Spatial Cookbook` is almost done!
- [book recommendation] `Teaching Tech Together`:
    + teachtogether.tech
- Angela talked about the challenges of super cryptic errors in spatial libraries and how she sees it as her job to make spatial libraries kind of "get out of the way" and get people thinking about the spatial problems
    + should donate the Ousterhout book. I think it has some principles that could help
