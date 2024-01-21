# E-Tech Retail Analysis Report
## Presented by: Ekene Christian Ikeakanam
___
## INTRODUCTION AND PROBLEM STATEMENT
___

![Picture1](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/5f4da8d5-2ad5-4d51-bcdb-f5e3d8792d41)

The E_Tech dataset provides comprehensive information about various aspects of a retail business. It consists of detailed information about annual sales such as order and shipping details, customer information, product characteristics, and financial metrics. Analyzing this dataset provides an opportunity to hone one's data analytics skills by unravelling valuable insights that contribute to informed decision-making and strategy formulation for the retail business.

Over the years, businesses encounter different forms of challenges which could be operational, increase in patronage, enhancing customer satisfaction, and maximizing profitability. The main objectives of embarking on this project is to identify patterns, trends, and opportunities within the dataset that provides key insights and possible solutions to these challenges. 
Businesses across various sectors often struggle with issues around inventory management, shipping strategies, customer segmentation, and optimal pricing. Analyzing the dataset can shed light on these areas and guide the business toward more effective and profitable practices.

Some Insights uncovered includes:
- Identify top-performing products and product categories.
- Analyze sales trends over time and highlight peak seasons (months / days) of high demand.
- Understand customer preferences particularly useful for tailoring marketing strategies.
- Analyze profit margins and impact of discounts on the overall profitability.
- Examine regional (State / Provincial) variations in sales and profitability.
- Identify opportunities for expansion or targeted marketing in specific regions.
- Effectiveness of discounts in driving sales.
- Identify most commonly used and effective shipping methods and prices
- Uncover rate of order fulfilment and returns respectively

## Dataset and Source of Data
___
The dataset consists of three tables (Orders, Reruned Orders, Regions) with columns capturing details related to orders, customers, products, shipping, and financial metrics. Each column holds valuable information that can be analyzed to understand and optimize different facets of the retail operation.
Below is a brief overview of key columns in the dataset:

**Order Details:**
- Row ID: A unique identifier for each row in the dataset.
- Order Priority: Priority assigned to orders, indicating their urgency or importance.
- Discount: The discount applied to products in an order.
- Status: Information on the status (Completed or Returned) of the order
- Order Date:  Date when the order was placed

**Shipping Information**
- Shipping Cost: The cost associated with shipping an order.
- Ship Mode: The mode chosen for shipping the order.
 - Ship Date: Date when order was shipped to customer

**Customer Information:**
- Customer ID: Unique identifier for each customer.
- Customer Name: The name of the customer.
- Customer Segment: Segmentation of customers based on certain criteria.

**Product Details:**
- Product Category and Sub-Category: Classification of products into categories and sub-categories.
- Product Name: The name of the product.

**Geographic Information:**
- Region: The geographic region where the order was placed.
- State or Province: The state or province associated with the order.

**Financial Metrics:**
Profit: The profit generated from the order.
Quantity Ordered New: The quantity of each product ordered.
Sales: The total sales value for the order.

## Demonstrated Skills
___

## 1. Data Gathering and Preparation

### 1.1 Import Datasets
The dataset, stored in an Excel file, comprises three tables: Orders, Returns, and Regions. To import the data into Power BI Desktop, the Get Data feature was utilized. Subsequently, the three necessary tables were selected and loaded into the Power Query editor for further transformation. The import storage mode was chosen to eliminate the need for data refreshes.

### 1.2 Merging of Tables
The merging process involved the following operations:

**Orders and Returns Tables:**
- An Inner Join was applied to the Orders and Returns tables to create a new query. This operation focused on matching records of returned orders using the Order ID as the key identifier on both tables.

**Orders and Regions Tables:**
- A Right Outer Join was executed to merge the Orders and Regions tables, resulting in a new query named "Regional Manager." This operation introduced an additional column containing information about regional managers for all records in the Orders dataset. The key identifier for this operation was the region on both tables.

Upon completing these merge operations, the query load was disabled for both new queries (tables) to finalize the data integration.

### 1.3 Data Cleaning and Transformation: 
Several data transformation procedures were applied to enhance the quality of the dataset, including:
- Identification and removal of unwanted columns to minimize the model size
- Rename columns and update data types as required
- Combining First Name and Last names on the Regions table onto a single column called Full Name
- Creation of additional columns: Season (Summer, Winter, Autumn or Spring) using the OrderDate column and Order Processing days which is the number of days between Order and Shipping Date
- Cleaning of data by dealing with missing / null values, removal of duplicates and ensured only valid records were added to the model.
- Checked the quality and distribution of data using Column Quality, Profile and Distribution feature in Power Query Editor.

## 2. Data Modelling
___
The restructuring of the dataset involved transforming the original model into a standard Star Schema, ensuring a more efficient and logical organization of data. DEfualt schema is displayed below
![Sales Order Model](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/dfd85fa1-0292-4c41-99bb-9abaf73cb465)


The key steps taken are detailed below:

### 2.1 Creation of a Date Table:
A dedicated Date Table was created using the Calendar function. This table includes all dates within the range of the MIN(Order Date) and MAX(Shipping Date) columns from the Orders table. The Date Table incorporates essential time-based attributes such as Order Date, Year, Month, Quarter, and Day. Establishing a relationship with the Order Date column and Shipping Date on the Orders table facilitates time intelligence analysis, enabling insights into trends, seasonality, and comparisons across different time periods.

### 2.2 Fact Table Modeling:
- **Orders Table:**
The Orders table serves as a primary fact table, capturing information related to customer orders. It includes data such as Order ID, Order Priority, Discount, Unit Price, Shipping Cost, Customer ID, Product details, Profit, and Sales.

- **Returns Table:**
The Returns table contains information about returned orders, including the Order ID and associated return status.

- **Returned Orders Table:**
A new table, Returned Orders, was created as a result of merging the Orders and Returns tables. This table helps link orders with their corresponding return information.

- **Regional Orders Table:**
The Regional Orders table was formed by merging the Orders table with the Regions table using a Right Outer Join. This operation introduced additional details about regional managers, enhancing the dataset's analytical capabilities.

### 2.3 Dimension Table Modeling:
- **Dates Table:**
The Dates table, created in the first step, functions as the primary dimension table. It provides a comprehensive set of date-related attributes crucial for time-based analysis.

- **Regions Table:**
The Regions table serves as another dimension table, offering details about different regions and their respective managers.

### 2.4 Relationship Establishment:
Relationships were established between the following tables:

- Orders table and Dates table (using Order Date and Date columns)
- Orders table and Returned Orders table (using Order ID)
- Orders table and Regions table (using Region)
- Returned Orders table and Returns table (using Order ID)
  
These relationships form the basis for creating powerful visualizations and conducting insightful analyses within Power BI, aligning with the principles of a Star Schema for optimal data modeling.

## 3. ANALYSIS AND VISUALIZATION
___
The E-Tech Retail Analysis project comprises three insightful reports: Sales, Profis, and Orders.

A pictorial overview of both reports is displayed below:
|Sales|Profit|Orders|
|----------|--------------|--------------|
|![SALES REPORT](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/e9aa9f62-c3a8-4ff2-ab80-e72e8ad238ea)|![PROFIT REPORT](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/e5960de7-8def-4ac3-b304-a86921a2e35a)|![ORDERS REPPORT](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/efbd524b-3e9e-4ae5-bac5-435b09db63b0)|

![SALES REPORT](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/e9aa9f62-c3a8-4ff2-ab80-e72e8ad238ea)
![PROFIT REPORT](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/e5960de7-8def-4ac3-b304-a86921a2e35a)
![ORDERS REPPORT](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/efbd524b-3e9e-4ae5-bac5-435b09db63b0)
