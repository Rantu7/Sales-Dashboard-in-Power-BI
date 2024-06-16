# <p align="center">Sales Dashboard in Power BI</p>

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
1.	Sales data folder from 2014 to 2017 (.csv)
2.	Categories (.xlsx)
3.	Geography(.xlsx)
4.	Product(.csv)
5.	Salesrep(.xlsx)
6.	Subcategories (.xlsx)

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

