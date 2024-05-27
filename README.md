#  Maven Toy Sales Analysis- Dashboard

📊 Thrilled to unveil my latest endeavour: a comprehensive Maven Toy Sales Analysis project focused on profit and loss comparison of  previous year accurately crafted using Power BI and Microsoft Excel! 🚀

 ## Here's what you can expect from this dashboard:

🛠️ Toolkit: Power BI, Microsoft Excel

📊 Datasets: Microsoft Excel

Project Overview:

Diving deep into Maven Toy Sales Analysis, this project revolves around dissecting sales performance and turnover, comparison with previous year sale details with precision.

Here's what you can expect from this dashboard:

•	Sliced date time stamps scroll through select the date we can have a sales data for the years and months/locations.	
•	Product line and average rating of the product it keeps changing according to the date.
•	Sales date wise – we can see number of store locations details during the particular time. 
•	Product wise YTD sales will get. 
•	Total sales by month and year details.
•	Store locations with accurate data. 
•	Faisal year details 
Date Cleaning process: 
During cleaning the data in power query – identified 4th data product cost and product price in $, power bi will not consider the symbol. 
Action took – replaced the $ with empty for both trimmed the data and placed in decimal.
We need to connect sales table and product table, go to home merge query together sales table and product table, choose product ID as a primary key -> joint kind Left outer   

![1](https://github.com/Mohanasundaram-Mohi/Sales-Analysis-/assets/168515064/b24b18a8-655f-4bec-9af7-a3f18e2b0daf)

Add custom column for total sales :

![1](https://github.com/Mohanasundaram-Mohi/Sales-Analysis-/assets/168515064/24079fde-95a6-491e-9356-ff46bea998b3)

Create a new table for date intelligence: 
Date = date = CALENDAR(min(sales[Date]), max(sales[Date]))

Reason for taking store opening date basically covers all the date.
New column for month-yr- Month-yr = FORMAT('date'[Date], "mmm-yy")
New column for fiscal year = start of year = STARTOFYEAR('date'[Date],"31/3")
New column for fiscal year = Fiscal year = YEAR('date'[start of year])
New column for quarter number = Qtr No = QUOTIENT(DATEDIFF('date'[start of year],'date'[Date],MONTH),3+1)

Data Relations: Model view 

![1](https://github.com/Mohanasundaram-Mohi/Sales-Analysis-/assets/168515064/d5f5c6ec-4beb-4b09-b3b6-afff948b06d6)

DAX Expressions: 
Create a table for Key measures = Table = ROW("column", BLANK())
Key measures = ROW("column", BLANK())
 
CARDS – 5 cards created 
1.	YTD sales = YTD sales = TOTALYTD(sum(sales[total sales]),'date'[Date],"31/3")
2.	Last Year YTD = CALCULATE([YTD sales],SAMEPERIODLASTYEAR('date'[Date]))
3.	MTD sales = TOTALMTD(sum(sales[total sales]),'date'[Date])
4.	Last Year MTD = CALCULATE([MTD sales],SAMEPERIODLASTYEAR('date'[Date]))  
5.	YTD growth = CALCULATE(DIVIDE(([YTD sales]-[Last Year YTD]),[Last Year YTD]))

![1](https://github.com/Mohanasundaram-Mohi/Sales-Analysis-/assets/168515064/d738f9c2-ea0f-48bf-be81-786076fea713)


![Screenshot (28)](https://github.com/Mohanasundaram-Mohi/Sales-Analysis-/assets/168515064/fa92fe0d-f5b0-453f-b943-596ce8484026)








 
