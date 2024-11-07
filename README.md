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

**Power Pivot & Dax**
* I created a data model in Power Pivot
* I was able to create calculated fields in Power Pivot to use for the pivot tables: such as Customer Count & Transaction Count.
``` DAX
  Customer Count:=DISTINCTCOUNT([Customer ID])
  Transaction Count:=COUNT([Customer ID])
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
* The lowest customer ranges include 18-24 years of age, and over 75 years of age, suggesting that their may be an opportunity to target and gain more of these aged customers.

![Age of Customers Chart]()
