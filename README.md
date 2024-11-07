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

#### Extract
* I first used Power Query to extract the original data () and create a query.

#### Transform
* Then I tranformed the query by changing column types to the correct type(currency for price columns).
* I added two new columns one for "Grand Total Purchase", which included adding "Total Price" and the "Add-on Total" together.
* The second coloumn was created "Add-on included" in order to show True or False on whether an Add-on was in the transaction.
  ```
  = Table.AddColumn(#"Changed Type1", "Add-on included", each if [#"Add-on Total"]>0 then true else false)
  ```

  
