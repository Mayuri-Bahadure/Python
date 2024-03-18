# Diwali Sales Analysis


## Problem Statement

Improve customer experience by analyzing sales data. Give suggestion to increase revenue.

## Data Prepration using Python
For data preparation their is CSV file which uploaded to jupyter notebook:
- Step 1: Import necessary libraries : 
In this step pandas, pandas, Matplotlib.pyplot ( to create plot) and seaborn.
- Step 2: Read CSV:
Use function read_csv.To avoide encoding error,"unicode escape" is used.
- Step 3: Delete Null columns:
First check for null columns using df.info() function. Their is some null columns named as status and unnamed1. To delete those columns use drop function, use axis=1 parameter to delete whole column and apply inplace=True to save changes.
- Step 4: Remove null values:
To check null values use function pd.insull(df).sum(). This function shows total null values for each column. It is found that their is 12 null values in columnncalled amount. Use dropna function to delete rows of null values.
- Step 5: Change Data type:
Amount column have float data type which was converted into integer using function df['Amount']= df['Amount'].astype('int').
- Step 6: Describes method returns:
use df.describe() function used to returns description of the data in the dataframe (i.e, count, mean, std, etc)

## Exploratory Data Analysis
- 1) Gender:
To plot the gender plot seaborn(sns) library is used, apply gender value on x axis and df is considered as dataframe to plot graph.
To get values on plot use containers and use ax.bar_label(bars) function.

Use groupby method to get total amount spend by male or female,
sales_gen = df.groupby(['Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.barplot(x = 'Gender',y= 'Amount',data = sales_gen)

- Insights: Most of the buyers are females and even the purchasing power of females are greater than men.

- 2) Age Group:
To plot the graph use countplot method and to divide on the basis of gender use hue method,
ax = sns.countplot(data = df, x = 'Age Group', hue = 'Gender')
for bar in ax.containers:
    ax.bar_label(bar)

Use groupby method to get total amount spend by different age group,
sales_age = df.groupby(['Age Group'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.barplot(x = 'Age Group',y= 'Amount' ,data = sales_age)

- Insights: Most of the buyers are of age group between 26-35 yrs female.

- 3) State:
To visualize total number of orders from top 10 states use group by method  and on the x axis 'state' value are plotted and on y axis 'orders' value are plotted.
sales_state = df.groupby(['State'], as_index=False)['Orders'].sum().sort_values(by='Orders', ascending=False).head(10)
sns.set(rc={'figure.figsize':(15,5)})
sns.barplot(data = sales_state, x = 'State',y= 'Orders')

To visualize total amount by sales from top 10 states use group by method and on the x axis 'state' value are plotted and on y axis 'amount' value are plotted.
sales_state = df.groupby(['State'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False).head(10)
sns.set(rc={'figure.figsize':(15,5)})
sns.barplot(data = sales_state, x = 'State',y= 'Amount')

- Insights: Most of the orders & total sales/amount are from Uttar Pradesh, Maharashtra and Karnataka respectively.

- 4) Marital Status:
To plot the marital_status plot seaborn(sns) library is used, apply marital_status value on x axis and df is considered as dataframe to plot graph.
To get values on plot use containers and use ax.bar_label(bars) function.
ax = sns.countplot(data = df, x = 'Marital_Status')
sns.set(rc={'figure.figsize':(5,10)})
for bars in ax.containers:
    ax.bar_label(bars)

To visualize marital_status by amount, use group by method and on the x axis 'marital_status' value are plotted and on y axis 'amount' value are plotted. Add hue method to get plot genderwise.
sales_state = df.groupby(['Marital_Status', 'Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.set(rc={'figure.figsize':(6,5)})
sns.barplot(data = sales_state, x = 'Marital_Status',y= 'Amount', hue='Gender')

- Insights: Most of the buyers are married (women) and they have high purchasing power.

- 5) Occupation:
To plot the occupation plot seaborn(sns) library is used, apply occupation value on x axis and df is considered as dataframe to plot graph.
To get values on plot use containers and use ax.bar_label(bars) function.
sns.set(rc={'figure.figsize':(20,5)})
ax = sns.countplot(data = df, x = 'Occupation')
for bars in ax.containers:
    ax.bar_label(bars)

To visualize occupation by amount, use group by method and on the x axis 'occupation' value are plotted and on y axis 'amount' value are plotted.
sales_state = df.groupby(['Occupation'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.set(rc={'figure.figsize':(20,5)})
sns.barplot(data = sales_state, x = 'Occupation',y= 'Amount')

- Insights: Most of the buyers are working in IT, Healthcare and Aviation sector.

- 6) Product Category:
To plot the product category plot seaborn(sns) library is used, apply product category value on x axis and df is considered as dataframe to plot graph.
To get values on plot use containers and use ax.bar_label(bars) function.
sns.set(rc={'figure.figsize':(20,5)})
ax = sns.countplot(data = df, x = 'Product_Category')
for bars in ax.containers:
    ax.bar_label(bars)

To visualize product id by orders, use group by method and on the x axis 'product id' value are plotted and on y axis 'orders' value are plotted.
sales_state = df.groupby(['Product_ID'], as_index=False)['Orders'].sum().sort_values(by='Orders', ascending=False).head(10)
sns.set(rc={'figure.figsize':(20,5)})
sns.barplot(data = sales_state, x = 'Product_ID',y= 'Orders')

- Insights: Most of the sold products are from Food, Clothing and Electronics category.

## Conclusion:
Married women age group 26-35 yrs from UP, Maharastra and Karnataka working in IT, Healthcare and Aviation are more likely to buy products from Food, Clothing and Electronics category.

