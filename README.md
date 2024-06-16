# <p align="center">Sales Dashboard in Power BI</p>
# <p align="center">![Screenshot_30](https://github.com/Rantu7/Sales-Dashboard-in-Power-BI/assets/167998182/c91daed5-720b-4b95-b50c-b224b6f83abe)</p>

## Objective
The objective of this project is to gain valuable insights by answering critical business questions posed by the owner. By utilizing the data transformation, visualization and DAX calculation functions available in Power BI, this project aims to present KPIs such as total revenue, total units sold, total profit, average sales etc. Time series analysis, Cost and revenue by location, revenue by product name and category etc. were also analyzed to find insights about the business and help facilitate data driven decision making.

## Business Requirements:
The sales report should be an interactive dashboard with filtering options and must contain the following information:
•	Sales KPI
•	YoY growth, MoM growth, QoQ growth
•	Best sales reps
•	Location wise sales information
•	Any other relevant graphs or charts to find insights

## Workflow:
The following steps were taken to complete the report :
1.	Data Collection
2.	Data Cleaning 
3.	DAX Calculations
4.	Data Modeling
5.	Data visualization
6.	Insights and feedback

  ## Data Collection:
The data was provided in separate files in multiple file types. A brief description about the data:

![Screenshot_32](https://github.com/Rantu7/Sales-Dashboard-in-Power-BI/assets/167998182/67a871e6-91a1-4533-8bed-533444d5b081)

## Data Cleaning:
The dataset was loaded into Power BI’s power query and cleaned to prepare for the next step. Data cleaning included the following steps:
•	Removing duplicates
•	Remove unnecessary columns
•	Handled blank and null values
•	Fixed data types 

## DAX Calculations
Data Analysis Expressions (DAX) is a formula expression language used to develop measures, calculated columns, calculated tables, and row-level security in Power BI. To fulfill the business requirements and conduct Data modeling, the following DAX formulas were used:
1. For time series analysis, a separate folder named 'Datemaster', that only contained tables with Year, Month, Quarter and Date was created. Months, years, dates and quarters were extracted using the below codes:
 
   ```dax
   DateMaster = CALENDAR(FIRSTDATE(Sales[Date]),LASTDATE(Sales[Date]))
    ```
   
     ```dax
   Month = FORMAT(DateMaster[Date],"MMM")
    ```
     
   ```dax
   MonthOrder = DateMaster[Date].[MonthNo]
    ```
   
   ```dax
   Quarter = QUARTER(DateMaster[Date])
    ```
    
    ```dax
   WeekDay = FORMAT( WEEKDAY(DateMaster[Date]),"DDD"))
    ```
    
   ```dax
   WeekNum = WEEKNUM(DateMaster[Date])
    ``` 
    
    ```dax
    Year = YEAR(DateMaster[Date])
    ```

DAX formulas to measure 'Month on Month' profit growth:
       
   ```dax
Prev Month Profit = CALCULATE(SUM(Sales[Gross Profit]), PREVIOUSMONTH(DateMaster[Date]))
MoM Growth = (SUM(Sales[Gross Profit])-[Prev Month Profit])/ [Prev Month Profit]
   ```
DAX formulas to measure  'Quarter on Quarter' revenue growth:
 ```dax
    Prev QTR = CALCULATE(SUM(Sales[Total Revenue]),PREVIOUSQUARTER(DateMaster[Date]))
QoQ Growth = (SUM(Sales[Total Revenue]) - [Prev QTR])/[Prev QTR]

   ```
DAX formulas to measure Total revenue, Total cost and Total profit:
    ```dax
  Total Revenue = Sales[Units]* RELATED('Product'[RetailPrice])
Total Cost = Sales[Units]*RELATED('Product'[StandardCost])
Gross Profit = Sales[Total Revenue]-Sales[Total Cost]
    ```

  Now the dataset is ready for Data Modeling step!
  
 ## Data Modeling: 
The purpose of data modeling in any data analysis project is to create relationship among multiple separate data tables to structure, organize, analyze and improve clarity of the data. For this project Sales data was considered as the 'Fact table' and the other tables were considered as 'Dimension table'. Dimension tables connect to the Fact table via each other using one to many relationship. Index columns were added as required to connect the tables. Below image shows the data before  modeling:
![model 01](https://github.com/Rantu7/Sales-Dashboard-in-Power-BI/assets/167998182/fe2029eb-1607-4a71-9713-b65eca4781ab)

Below image shows the data after modeling:
![model 02](https://github.com/Rantu7/Sales-Dashboard-in-Power-BI/assets/167998182/7a6da1dc-5d6e-46ec-923d-bdbe57ae2979)

 Now the data set is ready for visualization as the dimensions and fact tables are organized and connected among each other through data modeling.

## Data Visualization:
Relevant charts and graphs available in Power BI were used to create an appealing dashboard that fulfills all the business requirements. The main goal was to make the dashboard look aesthetic and easy to comprehend but also insightful. Below are screenshots of the report which can be downloaded here:

Page 1:
![Screenshot_30](https://github.com/Rantu7/Sales-Dashboard-in-Power-BI/assets/167998182/c91daed5-720b-4b95-b50c-b224b6f83abe)

Page 2:
![dashboard2](https://github.com/Rantu7/Sales-Dashboard-in-Power-BI/assets/167998182/89efe080-b116-4985-b92e-8df849ba69ac)

## Insights:
 Some insights that were found during the data analysis process:
1.	The company has a high revenue efficiency, with a total profit of $86.89 million from $126.01 million in revenue. This indicates a profit margin of approximately 68.96%, which is quite healthy. This suggests that the company is managing its costs effectively.
2.	The General category, contributing 64.46% of the total revenue, is the primary driver of sales. However, the Special category, while contributing less, might have higher margins or growth potential.
3.	Germany generated the highest revenue of $87.45 million. Czech Republic and Denmark earned $25.77 million and $12.79 million respectively. Although there is a huge difference in revenue, the revenue to cost ratio is almost around 3.2 for all three locations.
4.	According to the gross profit over time chart, the company has consistently accumulated lowest gross profit in February over the years. It has also generated the highest profit from June to August. Investigating which factors contribute to the high profits in these months and implementing or customizing them for February could help boost this month's profit.
5.	The time series analysis charts depict that the company accumulated lowest revenue and profit in 1st quarter of the year and the highest in the 3rd quarter. This indicates a seasonal pattern in the sales data. To lessen the impact of this seasonality, business strategies involving targeted marketing campaigns, stock adjustments, resource allocation, budget adjustments etc. could be implemented after proper investigation.

## Feedback:
1.	Adding data on customer demographics, preferences, and behavior could provide a more comprehensive view of the market and help in tailoring strategies to different customer segments.
2.	Comparing the company's performance against industry benchmarks or competitors could provide context to the data and highlight areas of competitive advantage or needed improvement.
3.	Since the company has a healthy profit margin, it is recommended to continuously monitor and optimize the cost structure to maintain the margins.

## Thank You!




