Popular Halloween Candy
October, 28 2020


Team C:
Sara Behnke
Cory Potter
Han Zhao


I. Introduction
This topic came at just the right time! We want to find out what the most popular Halloween candies are. This team will look at a survey of Halloween candy ranking and best selling candy data from Walgreen.com. The analysis will tell us:
Most popular Halloween candy by survey
Most popular Halloween candy by sales
Most popular Halloween candy by review ratings

II. Data source

a. Candy-data.csv(Kaggle.com) includes attributes for each candy along with its ranking. For binary variables, 1 means yes, 0 means no. The data contains the following fields:
chocolate: Does it contain chocolate?
fruity: Is it fruit flavored?
caramel: Is there caramel in the candy?
peanutalmondy: Does it contain peanuts, peanut butter or almonds?
nougat: Does it contain nougat?
crispedricewafer: Does it contain crisped rice, wafers, or a cookie component?
hard: Is it a hard candy?
bar: Is it a candy bar?
pluribus: Is it one of many candies in a bag or box?
sugarpercent: The percentile of sugar it falls under within the data set.
pricepercent: The unit price percentile compared to the rest of the set.
winpercent: The overall win percentage according to 269,000 matchups.

b. Walgreen’s website: https://www.walgreens.com/store/c/halloween-candy/ID=520931-tier3 (page is filtered by top sellers)

III. Data Extraction: we performed web scraping for Walgreen’s Halloween candy sales & rating data with beautiful soup.

a. Steps:
Create path to read Walgreen HTML file.
Create beautiful soup object.
Extract all candy listings on the current page (72).
Create a list of dictionaries to return brand name, description of candy and its rating.
Use try and except block to convert the non-review/rating results to NaN.

b. Challenges:
When we first ran our scrape file, Walgreens was only returning 8 results and we were unable to figure out why that was.
c. Solution:
We decided to copy the entire page’s outer html and save that to our repository. We used os to read in the html file and then we were able to perform our scraping.

IV. Data Transformation

a. Walgreen data transformation steps:
Create a dataframe with the list of dictionaries.
Drop any results that did not have a rating.
Break rating and reviews into two separate columns from the rating column.
Group by the brands to see the average brand rating and reviews.

b. Survey data transformation steps:
Remove special characters and replace with apostrophes.
Create a dataframe for chocolate candies.
Create a dataframe for fruity candies.
Create a dataframe of all other candy types.
Create a new table that only displays binary results.
Create a new table for percentages.

V. Load data to database

a. Walgreen data load steps: 
Create connection to postgresql.
Use pandas to load the scraped Walgreens dataframe into database.
Verify table was loaded successfully.
Use pandas to load brand averages dataframe to database
Verify table was loaded successfully.

b. Survey data load steps: 
Create connection to postgresql.
Use pandas to load binary_results dataframe into database.
Verify table was loaded successfully.
Use pandas to load percentage dataframe to database
Verify table was loaded successfully.






