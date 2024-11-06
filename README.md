# LITA-PROJECT-2


### Project Title: Customer Segmentation Analysis

### Project Overview
---
This project leverages on customer data to uncover behaviour patterns, track subscription types and identify trends in cancellations and renewals. 

### Data Source
---
The dataset used in this project is the LITA Capstone Dataset (Subscription Data). This Data was provided by our instructors specifically for analysis purposes, which helped to stimulate real-world scenarios for analysis.

### Tools Used
---
- Mircosoft Excel for Data Cleaning, Analysis and Visualization
- Structured Query Language (SQL) for Querying of Data
- Power Bi for Advanced Visualizations and Interactive Reports
- GitHub for Portfolio Building

### Data Cleaning and Prepartions
---
1. Data loading and Inspection
2. Data cleaning and formatting

### Exploratory Data Analysis
  ---
  Below are some of the question answerwed while exploring the Dataset;
- Microsoft Excel
  1. Analyze customer data using pivot tables to find subscription patterns.
  2. Calculate average subscription duration and identify the most popular subscription types.
  3. Create any other interesting reports

- SQL
  1. Retrieve total nmber of customers from each region.
  2. Find the most popular subscription type by the number of customers.
  3. Find customers who cancelled their subscription within 6 months.
  4. Calculate the average subscription duration for all customers.
  5. Find customers with subscriptions longer than 12 months.
  6. Calculate total revenue by subscription type.
  7. Find the top 3 regions by subscription cancellations.
  8. Finf the total number of active and cancelled aubscriptions.
 
- Power BI
  1. Build a power Bi dashboard that visualizes key customer segments, cancellations and subscription trends. Include slicers for interractive analysis.
 
### Data Analysis
---
1. Microsoft Excel Below are some analysis done on the data:

  ![alt text](<Active and canceled subscription by region.jpg>)
  ![alt text](<Active and canceled subscriptions by customers.jpg>)
  ![alt text](<Active and canceled subscriptions over the years.jpg>)
  ![alt text](<Average subscription duration.jpg>)
  ![alt text](<Customers by region.jpg>)
  ![alt text](<Monthly subscriptions.jpg>)
  ![alt text](<Popular subscription type by region.jpg>)
  ![alt text](<Popular subscription type.jpg>)


2.  SQL

Below are some queries used in the data analysis;
 ```SQL
SELECT * FROM  [dbo].[CustomerData]

---Total Number of Customer from each Region
select Region, COUNT(CustomerName) AS Totalcustomers
from [dbo].[CustomerData]
Group by Region 

----Most popular Subscription type by Customers
select top 1 SubscriptionType, Count(CustomerID)as NumberofCustomers
from [dbo].[CustomerData]
group by SubscriptionType
order by NumberofCustomers desc

---Total Revenue by Subscription Type
select SubscriptionType, SUM(Revenue) as TotalRevenue
from [dbo].[CustomerData]
group by SubscriptionType

---Top 3 Regions by Subscription Cancellations
SELECT TOP 3 Region, COUNT (*) AS Cancellations
from [dbo].[CustomerData]
where SubscriptionEnd is not null
Group by Region
order by Cancellations desc

----Total Number of Active and Canceled Subscription
SELECT CASE WHEN Canceled = 'TRUE' then 'CANCELED'
ELSE 'ACTIVE'
END AS SubscriptionStatus,
Count (*) as TotalSubscriptions From [dbo].[CustomerData]
GROUP BY CASE WHEN Canceled = 'TRUE' THEN 'CANCELED' ELSE 'ACTIVE'
END;

----Average Subscription Duration
select AVG(datediff(day,SubscriptionStart,isnull(SubscriptionEnd,getdate()))) 
as AverageDuration
from [dbo].[CustomerData]

---Customers who canceled their subscription within 6 months
select CustomerID, CustomerName, SubscriptionStart, Canceled from [dbo].[CustomerData]
where Canceled = 'TRUE'
AND DATEDIFF(month, SubscriptionStart, getdate()) <= 06 ;

---Customers with subscriptions longer than 12 months
select CustomerID, CustomerName, SubscriptionStart, Canceled 
from [dbo].[CustomerData]
where DATEDIFF(month, SubscriptionStart, getdate()) > 12
```

### Data Visualization
---
Below are some data visualizations done using the Power BI: 
  ![alt text](<Average subscription duration.png>)
  ![alt text](<Customer by region.png>)
  ![alt text](<Customer by subscription type.png>)
  ![alt text](<Subsription type by revenue.png>)

###
