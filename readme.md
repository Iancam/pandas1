# Project 12: Geography, and the World Wide Web

_taken from https://raw.githubusercontent.com/msyamkumar/cs220-f20-projects/master/p12/README.md_

Before you start the following assignment, you need to have some understanding of Pandas. You can [start off here](https://www.kaggle.com/residentmario/creating-reading-and-writing), or, if you feel ready to jump in to something a bit faster paced, [use this cheat sheet here](https://www.educative.io/blog/pandas-cheat-sheet).

## Learning Objectives

In this project, you will

- Gain more experience with reading and writing files
- Practice using a linter with your code
- Practice using Pandas with python
- Practice creating DataFrames

## Overview

For this project, you're going to analyze the whole
world!

Specifically, you're going to study various statistics for 174
countries, answering questions such as: _What is the correlation
between a country's literacy rate and GDP?_

To start, clone the repository. `git clone github.com/iancam/pandas1` You'll do all your work in main.ipynb.

# Data

For this project, you'll be using one large JSON file with statistics from
about 174 countries. We found them
[here](https://www.kaggle.com/fernandol/countries-of-the-world).
You will also extract data from a snapshot of
[this page](http://techslides.com/list-of-countries-and-capitals).

To get started, open up main, and run the notebook spot, and then the second. Great! What you should see are our two data tables

Some of the columns in the data require a little extra explanation:

- Area: measured in square miles
- Coastline: Ratio of coast to area
- Birth-rate: Births per 1000 people per year
- Death-rate: Deaths per 1000 people per year
- Infant-mortality: Deaths per 1000 births per year
- Literacy: (out of 100%)
- Phones: Number of phones per 1000 people

**DISCLAIMER**: This data is probably wrong in a lot of ways. We're using it to practice pandas.

# Testing

All the right answers can be found in `test.py`. If you're wondering if you did the right thing, take a look over there.

# Questions

#### #Q1: How many countries do we have in our dataset?

#### #Q2: what is the total population across all the countries in our dataset?

_Hint_: Review how to extract a single column as a Series from a
DataFrame. You can add all the values in a Series with the `.sum()`
method.

---

Use `capitals` and `countries` DataFrames to answer the following questions.

#### #Q3: What are the capital names in `capitals.json`?

Answer with an alphabetically-sorted Python list.

#### #Q4: What is the capital of Italy?

_Hint_: you can use fancy indexing to extract the row where the
`country` equals "Italy". Then, extract the `capital` Series, from
which you can grab the only value using `next(iter(...))`.

#### #Q5: Which country's capital is Brussels?

#### #Q6: Which 7 countries have the southern-most capitals?

Produce a Python list of the 7, with southernmost first.

_Hint_: look at the documentation examples of how to sort a
DataFrame with the [sort_values](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.sort_values.html) function.

#### #Q7: Which 10 countries have the capitals closest to the North Pole?

The expected output should be sorted according to the distance, with the closest captial at the start of the list.

#### #Q8: What is the smallest land-locked country in Asia?

A "land-locked" country is one that has zero coastline. Smallest is in terms of **area**.

#### #Q9: What is the largest coastal country in Asia?

A "coastal" country is one that has non-zero coastline. Largest is in terms of **area**.

#### #Q10: What is coastal country with the least population in South America?

#### #Q11: What is the distance between Camp Randall Stadium and the Wisconsin State Capital?

This isn't related to countries, but it's a good warmup for the next
problems. Your answer should be about 1.4339 miles.

Assumptions:

- The latitude/longitude of Randall Stadium is 43.070231, -89.411893
- The latitude/longitude of the Wisconsin Capital is 43.074645, -89.384113
- Use the Haversine formula: [http://www.movable-type.co.uk/scripts/gis-faq-5.1.html](http://www.movable-type.co.uk/scripts/gis-faq-5.1.html)
- The radius of the earth is 3956 miles
- You should answer in miles

If you find code online that computes the Haversine distance for you,
great! You are allowed to use it as long as (1) it works and (2) you
cite the source with a comment. Note that we won't help you
troubleshoot Haversine functions you didn't write yourself during
office hours, so if you want help, you should start from scratch on
this one.

If you decide to implement it yourself (it's fun!), here are some tips:

- Review the formula: [http://www.movable-type.co.uk/scripts/gis-faq-5.1.html](http://www.movable-type.co.uk/scripts/gis-faq-5.1.html)
- Remember that latitude and longitude are in degrees, but sin, cos, and other Python math functions usually expect radians. Consider [math.radians](https://docs.python.org/3/library/math.html#math.radians)
- This means that before you do anything with the long and latitudes make sure to convert them to radians as your FIRST STEP

#### #Q12: What is the distance between Germany and Norway?

For the coordinates of a country, use its capital.

#### #Q13: What are the distances between Italy, United Kingdom and Germany?

Your result should be DataFrame with 3 rows (for each country) and 3
columns (again for each country). The value in each cell should be
the distance between the country of the row and the country of the
column. For a general idea of what this should look like, open the
`expected.html` file you downloaded. When displaying the distance
between a country and itself, the table should display NaN (instead of
0).

#### #Q14: What is the distance between every pair of countries in the North American continent?

Your result should be a table with 24 rows (for each country) and 24
columns (again for each country). The value in each cell should be
the distance between the country of the row and the country of the
column. For a general idea of what this should look like, open the
`expected.html` file you downloaded. When displaying the distance
between a country and itself, the table should display NaN (instead of
0).

#### #Q15: What is the most central country in the North American continent?

This is the country that has the shortest average distance to other countries in North America.

_Hint 1_: Check out the following Pandas functions:

- [DataFrame.mean](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.mean.html)
- [Series.sort_values](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.sort_values.html) (note this is not the same as the DataFrame.sort_values function you've used before)

_Hint 2_: A Pandas Series contains indexed values. If you have a
Series `s` and you want just the values, you can use `s.values`; if
you want just the index, you can use `s.index`. Both of these
objects can readily be converted to lists.

#### #Q16: What is the least central country in North America?

This one has the largest average distance to other countries.

#### #Q17: How close is each country in North America to its nearest neighbor?

The answer should be in a table with countries as the index and two
columns: `nearest` will contain the name of the nearest country and
`distance` will contain the distance to that nearest country.

_Hint 1_: Find a Series of numerical data you can experiment with
(perhaps from one of the DataFrames you've been using for this
project). If your Series is named `s`, try running `s.min()`.
Unsurprisingly, this returns the smallest value in the Series. Now
try running `s.idxmin()`. What does it seem to be doing?

_Hint 2_: If you run `df.min()` on a DataFrame, Pandas applies that
function to every column Series in the DataFrame. The returned value
is a Series. The index of the returned Series contains the columns
of the DataFrame, and the values of the returned Series contain the
minimum values. If you run `df.idxmin()` on a DataFrame, the
returned values contain indexes from the DataFrame.

_Hint 3_: If you get an error message about dtypes when running
idxmin, make sure your DataFrame contains only floats (use
`df.astype(float)` if necessary).

#### #Q18: How far is each country in North America to its furthest neighbor?

The answer should be in a table with countries as the index and two
columns: `furthest` will contain the name of the furthest country and
`distance` will contain the distance to that furthest country.

#### #Q19: For `birth-rate` and `death-rate`, what are various summary statistics (e.g., mean, max, standard deviation, etc.)?

_Format_: Use the
[describe](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.describe.html)
function on a DataFrame that contains `birth-rate` and `death-rate`

columns. You may include summary statistics for other columns in
your output, as long as your summary table has stats for birth-rate and
death-rate.

#### #Q20: BeautifulSoup

Very often, you don't have data in nice json format like `capitals.json`. Instead data needs to be scraped from a webpage and requires some cleanup.
This is a long but fun exercise where we will do the same by scraping this webpage: http://techslides.com/list-of-countries-and-capitals.
Our `capitals.json` file was created from this same webpage.
You need to write the code to create `capitals.json` file from this table yourself.
Start by installing BeautifulSoup using pip, as discussed in class (learn how to install from [lecture slides](https://www.msyamkumar.com/cs220/f20/materials/lec_32_F20.pdf)).

Then call `download('capitals.html', 'https://raw.githubusercontent.com/msyamkumar/cs220-f20-projects/master/p12/techslides-snapshot.html')`
to download the webpage. Note that this code is not downloading the original webpage, but a snapshot of it (this is to avoid creating
excessive load on their servers). You can open `capitals.html` and make sure that this page looks fine.

Now do the following:

- Read from `capitals.html` and use beautiful soup to convert the html text to soup.
- Find the table containing the data (Hint: .find() or .find_all() methods can be used).
- Find all the rows in the table (Note: rows are inside 'tr' html tag and data is in 'td' tag).
- Create a dictionary containing country name, capital and location coordinate and then create a list of dictionaries for all the countries.
- **Careful!** This web page has more countries than `countries.json`. We will ignore the countries that are not in that file. You need to filter and keep only the 174 countries whose names also appear in `countries.json`. The column names should be consistent with the original `capitals.json`.
- Save this list into file titled `my_capitals.json`. You can use json.dump() method.

Your answer will be your data from your constructed `my_capitals.json` file read in using `open("my_capitals.json", "r").read()`

This answer should look like capitals.json however this time you have parsed the data using BeautifulSoup. Note the data type of columns `latitude` and `longitude` should be `float`.

### After you add your name and the name of your partner to the notebook in the first cell, please remember to Kernel->Restart and Run All to check for errors then run the test.py script one more time before submission. To keep your code concise, please remove your own testing code that does not influence the correctness of answers.

Cheers!
