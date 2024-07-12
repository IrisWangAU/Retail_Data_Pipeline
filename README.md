<div align="center">
  <a href="#">
    <img src="https://github.com/IrisWangAU/Retail_Data_Pipeline/blob/main/asset/walmartecomm.jpg" alt="Banner" width="720">
  </a>

  <div id="user-content-toc">
    <ul>
      <summary><h1 style="display: inline-block;"> Analysis of Walmart E-Commerce Sales</h1></summary>
    </ul>
  </div>
  
  <p>Data Pipeline for sale data in Parquet and CSV files</p>
</div>
<br>

## 📝 Table of Contents
1. [Introduction](#introduction)
2. [Key Insights](#key-insights)
3. [Project Architecture](#project-architecture)  
  3.1. [Data extraction](#data-extraction)  
  3.2. [Data Transformation](#data-transformation)  
  3.3. [Data Loading](#data-loading)
  3.4. [Pipeline Testing](#pipeline-validate)  
  3.5. [Data Reporting](#data-reporting)
  
4. [Technology used](#technology)
5. [Contact](#contact)

<br>

<a name="introduction"></a>
## 🔬 Project Overview 

Walmart is the biggest retail store in the United States. Just like others, they have been expanding their e-commerce part of the business. By the end of 2022, e-commerce represented a roaring $80 billion in sales, which is 13% of total sales of Walmart. One of the main factors that affects their sales is public holidays, like the Super Bowl, Labour Day, Thanksgiving, and Christmas. 

In this project, I build a ETL data pipeline for the analysis of supply and demand around the holidays, along with conducting a preliminary analysis of the data.

<br>

### 💾 Dataset

There are two data sources: grocery sales and complementary data.

The `grocery_sales` table have the following features:

<br>

#### **`grocery_sales`**
- `"index"` - unique ID of the row
- `"Store_ID"` - the store number
- `"Date"` - the week of sales
- `"Weekly_Sales"` - sales for the given store

The `extra_data.parquet` file contains complementary data:

#### **`extra_data.parquet`**
- `"IsHoliday"` - Whether the week contains a public holiday - 1 if yes, 0 if no.
- `"Temperature"` - Temperature on the day of sale
- `"Fuel_Price"` - Cost of fuel in the region
- `"CPI"` – Prevailing consumer price index
- `"Unemployment"` - The prevailing unemployment rate
- `"MarkDown1"`, `"MarkDown2"`, `"MarkDown3"`, `"MarkDown4"` - number of promotional markdowns
- `"Dept"` - Department Number in each store
- `"Size"` - size of the store
- `"Type"` - type of the store (depends on `Size` column)

The two files need to be merged and manipulated. The transformed DataFrame can then be stored as the `clean_data` variable containing the following columns:
- `"Store_ID"`
- `"Month"`
- `"Dept"`
- `"IsHoliday"`
- `"Weekly_Sales"`
- `"CPI"`
- `"Unemployment"`

After merging and cleaning the data, the monthly sales of Walmart are stored  as the `agg_data` variable that look like:

|  Month | Weekly_Sales  | 
|---|---|
| 01  |  33174.178494 |
|  02 |  34333.326579 |
|  ... | ...  |  

Finally, the `clean_data` and `agg_data` files are stored as csv files.

<br>

### 🎯 Project Goals

- Load data from Parquet and CSV files into DataFrame.
- Transform the data into the desired clean format.
- Calculate the average weekly sales by month.
- Save the cleaned data into a CSV file.
- Validate the existence of the final cleaned data in the CSV file.
- Create a data visualization in Power BI.

<br>

<a name="key-insights"></a>
## 🕵️ Key Insights

- 💸 **Total Sales by Month**
  - The total E-commerce revenue for Walmart across all files amounts to 3.63 billion.
  - Among all the months, Walmart has the highest revenue in April (0.35 billion), followed by July (0.34 billion) and December (0.33 billion). January has the lowest revenue, at 0.17 billion
 
- 🌍 **Average Weekly Sales by Month**
  - The average weekly sales are significantly impacted by holidays such as the Super Bowl, Labor Day, Thanksgiving, and Christmas.
  - In December, Walmart experiences the highest weekly sales (over 38K), followed by November (over 36K).
  > This trend can be attributed to increased consumer purchasing at Walmart in preparation for Christmas.

<br>

<a name="project-architecture"></a>
## 📝 Project Architecture

<br>

<a name="data-extraction"></a>
### 📤 Data Ingestion
- Extract Data from source file

![extract](https://github.com/IrisWangAU/Retail_Data_Pipeline/blob/main/asset/Extract.PNG)

<br>

<a name="data-transformation"></a>
### ⚙️ Data Transformation

- Fill NAs in Date, CPI, Unemployment with the last non-null values.
- Drop any rows with missing values in weekly sales and keep only rows with sales revenue above 10K.
- Create a new column for Month from the Date Column.
- Create a new Data Frame for Average Weekly Sales by Month using aggregation.

![Transform](https://github.com/IrisWangAU/Retail_Data_Pipeline/blob/main/asset/Transform.PNG)

<br>

<a name="data-loading"></a>

### 📥 Data Loading

- Save the Cleaned and Aggregated Data into CSV files

![SaveData](https://github.com/IrisWangAU/Retail_Data_Pipeline/blob/main/asset/savedata.PNG)

<br>

<a name="pipeline-validate"></a>

### ⚙️ Pipeline Testing

- Create a function to validate the existence of cleaned data and aggregated data files in the path
- Use Try-Except to run pipeline

![validate](https://github.com/IrisWangAU/Retail_Data_Pipeline/blob/main/asset/validate.PNG)
![pipelinerun](https://github.com/IrisWangAU/Retail_Data_Pipeline/blob/main/asset/pipelinerun.PNG)

<br>

<a name="data-reporting"></a>
### 📊 Data Reporting
- Connect PowerBI with cleaned and aggregated data to perform analysis

![salesreport](https://github.com/IrisWangAU/Retail_Data_Pipeline/blob/main/asset/WalmartSalesReport.PNG)


<br>

<a name="technology"></a>

### 🛠️ Technologies Used

- **Data Source**: csv and parquet files
- **Data Extraction**: Python Pandas Package
- **Data Transformation**: Pandas DataFrame, Python programming
- **Data Loading**: Python Pandas
- **Data Visualization**: PowerBI
- **Pipeline Testing**: Python Logging package

<br>

<a name="contact"></a>

## 📨 Contact Me

[LinkedIn](https://www.linkedin.com/in/iriswangau/) •
[Gmail](iriswang.mel@gmail.com)
