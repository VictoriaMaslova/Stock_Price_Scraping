# Scraping Yahoo Finance’s most active stocks
I have designed mechanisms which scrap the most active stocks of yahoo finance using beautifulsoup. The scraped data output is later analysed, enabling me to compare the results.

Dependencies for creating virtual environment described below.
Furthermore, there is a Makefile created into the repository and processes mentioned below handled automatically:

* Creating virtual environment,
* Installing required packages from requirements.txt file,
* Clean virtual environment.


# Beautiful Soup

For this project, in addition to other libraries BeautifulSoup library was used. Another python library, requests , gets the html of the webpage at url ```https://finance.yahoo.com/most-active```, which is later parsed by BeautifulSoup.
The webpage has a table with 24 rows and numerous columns. Every row has the symbol attribute, which is later used finding the links to the company’s yahoo-finance page.

"https://finance.yahoo.com/quote/" + symbol + "?p=" + symbol

For every link defined in such a way, first the html copy of the page via the link is requested and then parsed. The variables such as ```Previous Close```, ```Open```, etc are distributed among two tables: table 1 and table 2. Within their respective tables, every variable is specified by data-test attribute, allowing me to specify and extract a variable of interest one at a time.
The extracted values are appended to already created lists, finally making up a dataframe with the variable names as column headers and the values as a column vector. The dataframe is exported to the csv file stocks_bs.csv.

To run the bs.py file on the command line, use the command
```
# for python3 users
…. : ~<project_root>$ python3 bs.py 
# for python2 users
…. : ~<project_root>$ python bs.py 
```
