# Web Scrapping: 

## DESCRIPTION
### Step:1 Import Necessary Libraries
Import Pandas, numpy, BeutifulSoup and Request libraries.

Function Of Libraries:
1) Numpy: NumPy provides support for creating and manipulating arrays, which are more efficient than Python lists for numerical operations.
2) Pandas: Pandas provides the DataFrame and Series data structures, which are designed for efficient data manipulation and analysis.
3) BeutifulSoup: Beautiful Soup is used for parsing HTML and XML documents, making it easy to extract data from web pages.
4) Requests:  Requests is used to send HTTP requests to web servers and receive responses.

### Step:2 Get URL Access:
Copy URL of the products from the website, and apply request function to get content. To create soup use command, (r.content, " html.parser")

### Step:3 Iterate through multiple pages:
To iterate through multiple pages inspect the page of website and get anchor tag of the next button which is in html. Use href to get link of page. Use cnp(complete next page) variable to get full link , website link+ np (above created variable)

### Step:4 Create Loop :
Use For loop to obtain data of multiple pages. Use range of (2, 10) and add str(i) to the link.

### Step:5 Create empty list:
Create empty list of product name, prices, description and reviews.

### Step:6 Create box variable:
Box variable is created to avoide the additional information of other products from the website.

### Step:7 Find name of products:
Create names variable, use box variable and find_all function, find div tag and class from html code of website. Use for loop method and append method to get names.

### Step:8 Find prices of products:
Create prices variable, use box variable and find_all function, find div tag and class from html code of website.Use for loop mathod and append method to get all names.

### Step:9 Find description of products:
Create new variable called as desc, but in case of description instead of a div tag their is ul tag in the html code of website. Use for loop mathod and append method to get all names.

### Step:10 Find Reviews of products:
Create reviews variable, use box variable and find_all function, find div tag and class from html code of website.Use for loop mathod and append method to get all names.

### Step:11 Create same lenght of all list:
while creating the csv it is found that some list are shortened than others, to make them same lenght create new variable max_lenght in which maximum length among four lists (Product_name, Prices, Description, Reviews) and then extends each of these lists with None values to make them all the same length as the maximum length. This ensures that each list has the same number of elements, filling in any missing values with None.

### Step:12 Generate data DataFrame:
Create dictionary and add key values and list of that key value.

### Step:13 Convert to CSV
