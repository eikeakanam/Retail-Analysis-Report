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
The restructuring of the dataset involved transforming the original model into a standard Star Schema, ensuring a more efficient and logical organization of data.

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
The default and updated model schema is displayed below

|Default|Updated|
|----------|--------------|
|![Sales Order Model](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/dfd85fa1-0292-4c41-99bb-9abaf73cb465)|![Model11](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/a95198dc-2aee-44aa-a6d1-3d64ea7c6572)|

## 3. ANALYSIS AND VISUALIZATION
___
The E-Tech Retail Analysis project comprises three insightful reports: Sales, Profis, and Orders.

A pictorial overview of the reports is displayed below:
|Sales|Profit|Orders|
|----------|--------------|--------------|
|![Saless](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/fe2ce25c-3bdb-4968-803c-2fc0164ce2f9)|![PROFIT REPORT](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/e5960de7-8def-4ac3-b304-a86921a2e35a)|![Orderss](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/9b081f4a-eb04-403a-a682-1a18bf37c7e7)|

### 3.1 Sales Report
### Key Insights

**Sales Overview:**
- Cumulative sales from 2000 to 2023 reached $8.9 million, with an average annual sale of $2.2 million and a remarkable year-over-year growth rate of 41.8% over the four-year period.
- Approximately $321,000, or 3.6% of total sales, were returned, resulting in a net sales figure of $8.6 million, representing 97% of the total sales from 2020 to 2023.
- Total sales for the current year (2023) stand at $2,852,360, marking a substantial 32% increase compared to the average annual sales and a notable 27.9% growth compared to the total sales for the same period in the previous year (2022).
- Net sales for December 2023 amount to $321,611, reflecting a 14.3% decrease from November 2023 but showing a 15.9% improvement from December 2022.

![S_Dashboard](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/0efb3cfe-7b5a-4cac-acb2-32b219bfa5c8)

**Sales Trends:**
- Peak sales occur over the weekend, with Saturday and Sunday collectively contributing 32% ($2.8 million) to the total sales.
- The last quarter of the year sees the highest sales, with November, October, and December leading in terms of revenue.

**Customer Segmentation:**
- Corporate customers contribute significantly, accounting for around 38.5% ($3 million) of total sales from 2020 to 2023, closely followed by Home Office customers, contributing 24.1% ($2 million).
- Customers across all four segments spent the most on technology related products then furniiture.
- The top three customers are Gordon Brandt, Glen Caldwell, and Rosemary O'Brien.

![Sales 1](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/b83af73e-f360-4245-81e7-1be44d93d705)

**Regional Performance:**
- Sales distribution across the Central, East, and West regions is relatively balanced, with the Central region leading at approximately 28% and total sales of $3 million.
- In the Central region, 44% of total sales were attributed to Technology products.
- California (CA), New York (NY), and Illinois (IL) lead in terms of revenue.
  
**Product Category Insights:**
- Technology products and Furniture dominate product categories, with technology products generating about $4 million, representing 39.3% of total sales, and Furniture contributing 35% with a total sales figure of approximately $3 million.
- Top three products by total sales are Global Troy Tilter, Riverside Palais Bookcase, and Canon advanced copier.

![Sales2](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/2dc844ec-d481-4027-bb20-50ccc339ca5e)

### 3.2 Profits Report
### Key Insights

**Profit Analysis:**
- The total profit for the period is $1,312,442, exhibiting a robust year-over-year growth of 45.6%.
- Profits consistently peak in the fourth quarter (October - December), aligning with the period of highest sales.
- The most profitable products are Global Troy Tilter, Fellowes PB500, and GBC Docubind Machine.
- Technology products emerge as the most profitable across most regions, except the South

![P_Dash](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/686dff98-7c83-4d52-81ea-1589e54192b1)

**Returns Impact:**
- Returns impacted profits, resulting in $22,535 in returned profits. The net profit, however, remained strong at $1,289,907.
Profit Margins:
- The profit margin stands at 14.7%, showcasing the profitability of the business operations.

**Yearly and Monthly Performance:**
- The net profit for the current year (2023) is $435,653, reflecting a substantial 23.2% increase compared to the same period last year (2022).
- In December 2023, net profit reached $74,728, indicating a 26.5% increase from the same month in the previous year and a 26.6% decline from November 2023.
Profit Margin Trend:
- Over the years, there has been a consistent and steady increase in the profit margin, emphasizing the efficiency and effectiveness of the business.

![Profit1](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/f0eca61d-1cc0-4ad8-bec8-f63e4a9b9a13)

**Regional Profit Contributions:**
- The Central region dominates profit contributions, accounting for 40% of the total profits, closely followed by the East region with $378,000.
- The top three states contributing the most profits are Illinois (IL), New York (NY), and Texas (TX).

**Discount and Sales Relationship:**
- There is a clear correlation between discounts and sales, indicating that products with lower discounts result in higher sales and, consequently, higher profits.

![PRofit2](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/d0cfa633-7dd0-4b28-bf71-01a89432c8cf)

### 3.3 Orders Report
### Key Insights
**Order Fulfilment and Returns Analysis:**

- The total number of orders processed is 9,426, with only 98 orders returned and 9,328 successfully fulfilled.
Fulfilment Rates:
- The average order fulfilment rate is an impressive 98.8%, highlighting the efficiency of order processing. The return rate is low, standing at about 1.2%.
- It takes an average of 2 days to complete the processing of an Order from Order Date to Shipping date.
- The highest order fulfilment rate was recorded in the year 2020 with 99.2% and the lowest in the year 2021 at 98.7%.
- There was a 0.1% decline in the fulfilment in the current year 2023 when compared to the same period the previous year 2022.
- The most returns occured in the current year 2023 as 33 orders were unfilfiled. 

![Orders1](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/6052394f-d10d-4455-b309-9583bde469b8)

**Customer Segment Analysis**
- Corporate customers placed and completed the most orders over this period 
- Approximate 29% of the total returs were from orders placed by Home Office customers, closely followed by 27% from Small Businesses. 

**Regional Performance:**

- Regional analysis indicates that the Central region boasts the highest order fulfilment rate at 97%, while the South region experiences a slightly lower rate at 94%.
- The Central region dominates order distribution, contributing 30.7% of the total orders, closely followed by the East region.
- The West region records the highest number of returned orders, constituting approximately 44% of the total returns, closely followed by the East region.
- In terms of specific locations, the highest orders were received from customers in CA, TX, IL, NY and Fl respectively. Orders from these five states accounted for about 38% of the total orders.

![Orders2](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/476ee24b-d2b8-4914-8c15-ebef89b3266e)

**Product Preferences:**
- Across all regions, technology products emerge as the most ordered items, indicating consistent customer demand.
- Most ordered items are Global Leather Tilter, Bevis Conference Tables and Boxoffice Meeting Table while the highest returned products were: 80Min Slim Jewel Case CD-R, Eldon Simplefile Boxoffice, Xerox 197 and 1983 respectively

**Shipping Metrics:**
- The preferred ship mode for customers is Regular Air, accounting for approximately 75% of orders. Interestingly, Regular Air is also the most cost-effective shipping option, with an average cost of $6.9.
- The average shipping cost per order is $13, reflecting the overall cost efficiency of the shipping process.
- The average order processing time is 2 days, demonstrating a quick turnaround for order fulfilment.
- A significant portion (73%) of returned orders were originally shipped using Regular Air, suggesting a potential correlation between shipping method and returns.

![Orders3](https://github.com/eikeakanam/Retail-Analysis-Report/assets/75729930/c2bbb6dc-3f34-4ad8-8068-dbf3f583d631)
