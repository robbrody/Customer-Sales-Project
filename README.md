# Customer-Sales-Project

## Introduction

For this project, I began with a dataset from Kaggle containing 20,000 transactions representing sales for an online retailer spanning from September 2023 to September 2024. My analysis aimed to answer key questions about customer demographics, purchasing patterns, product performance, and shipping details. I utilized Excel for data exploration and visualization, leveraging tools such as Power Query, Power Pivot, DAX, pivot tables, and pivot charts to uncover insights and present findings effectively.

### Questions to Analyze

To understand the data form this online retailer, I asked the following:

1. **What is the age of our customers?**
2. **How many purchases are Loyalty Members making?**
3. **How are our customers shipping their purchase?**
4. **How many purchases included an Add-on?**
5. **How do sales volume and revenue vary across products?**

### Excel Skills Used

The following Excel skills were utilized for analysis:

* Pivot Tables
* Pivot Charts
* DAX (Data Analysis Expressions)
* Power Query
* Power Pivot

### Customer purchase behavior - Electronic Sales Data Dataset

The dataset used for thsi project was found on Kaggle. This dataset contains sales transaction records for an electronics company over a one-year period, spanning from September 2023 to September 2024. It includes detailed information about customer demographics, product types, and purchase behaviors. The dataset includes 20,000 transactions.

### ETL (Extract, Transform, Load)
**Skill: Power Query**

#### Extract
* I first used Power Query to extract the original data () and create a query.

#### Transform
* Then I tranformed the query by changing column types to the correct type(currency for price columns).
* I added two new columns one for "Grand Total Purchase", which included adding "Total Price" and the "Add-on Total" together.
* The second coloumn was created "Add-on included" in order to show True or False on whether an Add-on was in the transaction.
  ```
  = Table.AddColumn(#"Changed Type1", "Add-on included", each if [#"Add-on Total"]>0 then true else false)
  ```
* I also filtered one transaction that contained N/A value out of the dataset.
  
![Applied Steps in Power Query](https://github.com/robbrody/Customer-Sales-Project/blob/main/images/Power_query_applied_steps.png)
  
#### Load
* Finally, I loaded the transformed query into the workbook to set the foundation for my analysis.

![Power Query Table](https://github.com/robbrody/Customer-Sales-Project/blob/main/images/Power_query_full.png)

## Question 1: **What is the age of our customers?**
**Skills: PowerPivot & DAX**

* I created a data model in Power Pivot
* I was able to create calculated fields in Power Pivot to use for the pivot tables: such as Customer Count & Transaction Count.
``` DAX
  Customer Count:=DISTINCTCOUNT([Customer ID])
```
* I also created a new column [Age Buckets] in Power Pivot in order to put the Age of Customers into Buckets for further analysis.
``` DAX
  = 
SWITCH(
    TRUE(),
    [Age] < 18, "<18",
    [Age] >= 18 && [Age] <= 24, "18-24",
    [Age] >= 25 && [Age] <= 34, "25-34",
    [Age] >= 35 && [Age] <= 44, "35-44",
    [Age] >= 45 && [Age] <= 54, "45-54",
    [Age] >= 55 && [Age] <= 64, "55-64",
    [Age] >= 65 && [Age] <= 74, "65-74",
    [Age] >= 75, "75+",
    "Unknown"
)
```
### Analysis
**Insights:**
* The majority of customers fall within the 35-44 and 65-74 age groups. These two groups have the highest number of customers, indicating that these are the primary segments for the business.
* The graph shows a relatively wide age range of customers, from 18-24 to 75+. This suggests that the product or service offered has a broad appeal across different generations.
* The lowest customer ranges include the 18-24 age group, and over 75+ age group, suggesting that there may be an opportunity to target and gain more customers in these age groups.

![Age of Customers Chart](https://github.com/robbrody/Customer-Sales-Project/blob/main/images/Age_of_customers.png)


## Question 2: **How many purchases are Loyalty Members making?**
**Skills: DAX & Pivot Tables**

* I used DAX in order to create the Total Transaction Count needed for the Pivot Table.
  ``` DAX
    Transaction Count:=COUNT([Customer ID])
  ```
* I added the Loyalty Member to the Columns, whcih is a Yes or No in the Data, and COnverted those to "Not a Member" and "Loyalty Member" in the Pivot Table for the visualization.
* I added the Purchase Date (Years) to the Rows of the Pivot Table in order to show time in a line graph.
* I finally added the Transaction Count to the Values in order to finalize the information needed for the chart.

### Analysis
**Insights:**
* The number of purchases made by Loyalty Members has significantly increased from 2023 to 2024. This indicates that the loyalty program is gaining traction and driving more customer engagement.
* From 2023 to 2024, there was a notable increase in purchases by Loyalty Members, accompanied by an even greater rise in purchases by non-members. This trend indicates growth in the Loyalty Member program, while also highlighting an opportunity to encourage more non-members to join.

![Purchases by Loyalty Members](https://github.com/robbrody/Customer-Sales-Project/blob/main/images/Loyalty_members.png)


## Question 3: **How are our customers shipping their purchase?**
**Skills: Pivot Tables & Pivot Charts**

* I added the Shipping Type from the Data Model into the Rows of the Pivot Table Fields
* I also brought in the Transaction Count Measure into the Values of Pivot Table, and converted the Value Field Settings to show % of Grand Total instead of the counts.

![Shipping Value Field Settings]()
* I then Sorted the Pivot Table to show the largest values first to format the Pivot Chart.

### Analysis
**Insights:**
* Standard shipping is the most popular choice among customers, accounting for approximately 35% of all shipments. This suggests that customers are generally prioritizing cost-effectiveness over speed.
* Express, Overnight, Same Day, and Expedited shipping options have similar usage rates, each accounting for around 16-17% of shipments. This indicates that customers are willing to pay a premium for faster shipping when needed, but there's no clear preference for one expedited option over another.

![Shipping Perccentage]()
