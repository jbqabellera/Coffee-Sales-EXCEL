# Coffee Sales Dashboard

## Task 

The client wants to know:
1. What is our best-selling coffee product?
2. Which region/s show/s a potential opportunity where we can expand to? 
3. Who are our loyal customers? What are the characteristics of people who don't have a loyalty card? We need to develop a different strategy for them.
4. I want to reward our Top 5 customers. Create a list of their names.

## Data

The data includes three sheets:
- Orders - List of coffee orders, when it was bought, who bought it, what they bought, and how many
  - OrderID, Order Date, CustomerID, ProductID, and quantiy
- Customers - Database of customer information
- Products - Information of every product that we offer
  - Coffee Type, Roast Type, Size, Unit Price, Price per 100g, Profit
 
## Data Cleaning

Step 1. Duplicate and create a working sheet. This is where the magic will happen.
Step 2. Populate the following columns using XLOOKUP and INDEX(MATCH)

  Customer Name
  ```
  =XLOOKUP(C2,customers!$A$1:$A$1001,customers!$B$1:$B$1001,,0)
  ```

  Email
  ```
  =IF(XLOOKUP(C2,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0)=0, "",XLOOKUP(C2,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0))
  ```

Country
```
=XLOOKUP(C2,customers!$A$2:$A$1001,customers!$G$2:$G$1001,,0)
```

Step 3. Use INDEX and MATCH to populate the other columns easily. Drag right and down to auto-fill the cells.

Coffee Type
```
=INDEX(products!$A$1:$G$49,MATCH($D2,products!$A$1:$A$49,0),MATCH('Working Sheet'!I$1,products!$A$1:$G$1,0))
```

![(Coffee GIF.gif)]

Sales
```
Multiply the quantity bought ("Quantity") with the Unit Price.
```
Step 3. Create a new column for Coffee Type Name and Roast Type Name to make it easy to understand.

Coffee Type Name
```
=IF(I2="Rob", "Robusta",IF(I2="Exc","Excelsa",IF(I2="Ara", "Arabica",IF(I2="Lib","Liberica",""))))
```

Roast Type Name
```
=IF(J2="M", "Medium",IF(J2="L", "Light",IF(J2="D", "Dark")))
```

Step 4. Add a new column for "Loyalty Card."

```
=XLOOKUP([@[Customer ID]],customers!$A$1:$A$1001,customers!$I$1:$I$1001,,0)
```

Step 5. Double-check the data. Use Filters.

Step 6. Edit the formatting.

Step 7. Create pivot tables, charts, and slicers.

Step 8. Create the dashboard.

## Coffee Sales Dashboard

[(https://1drv.ms/x/c/492367e7aa5d37f3/IQO9yw-FvVX7RohWBleLMr9aAV7nxRJDAQ4Ycvrc3yWjOKc)]
