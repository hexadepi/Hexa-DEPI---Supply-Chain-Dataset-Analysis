Team: Hexa  
Project: Supply chain  
Members:  
  
1.Anas Hossam Hafez  
2.Ahmed Abdelmoniem Hussein  
3.Hazem Mohamed Refaat  
4.Salma Mohamed Moustafa  
5.Maryam Ahmed Fathy  
6.Maryam Osama Mohammed  
PROJECT DOCUMENTATION
MEASURES CREATED (12 Total)

1. Total Orders = COUNTROWS('Purchase_Orders')
2. Total Cost = SUM('Purchase_Orders'[TotalCost])
3. Average Order Value = DIVIDE([Total Cost], [Total Orders], 0)
4. Total Suppliers = DISTINCTCOUNT('Supplier_Master'[SupplierID])
5. Avg Lead Time = AVERAGE('Supplier_Performance'[AverageLeadTime_Days])
6. Avg Quality Score = AVERAGE('Supplier_Performance'[QualityScore])
7. On-Time Delivery Rate = AVERAGE('Supplier_Performance'[OnTimeDeliveryRate]) * 100
8. Total Sales Quantity = SUM('Customer_Sales_Orders'[Quantity])
9. Total Sales Orders = COUNTROWS('Customer_Sales_Orders')
10. Total Shipments = COUNTROWS('Shipment_Tracking')
11. Delivered Shipments = CALCULATE(COUNTROWS('Shipment_Tracking'), 'Shipment_Tracking'[Status] = "Delivered")
12. Delivery Success Rate = DIVIDE([Delivered Shipments], [Total Shipments], 0) * 100


All measures stored in dedicated Measures table (best practice).
DASHBOARD PAGES & VISUALS
Page 1: Supply Chain Overview

    Line Chart: Total Sales Orders by Month

    Column Chart: Total Cost by Supplier
    

    Pie Chart: Purchase Order Status Distribution

    (Original plan had KPI cards but switched to charts for data visibility)

Page 2: Supplier Performance Analysis

    Table: Supplier Master data (SupplierName, Country, OnTimeDeliveryRate, QualityScore, AverageLeadTime_Days)

    Bar Chart: On-Time Delivery Rate by Supplier

    Scatter Chart: Quality Score vs Average Lead Time (with SupplierName legend)

    Slicer: Country filter (optional interactivity)

Page 3: Sales Orders Analysis

    Line Chart: Total Sales Orders by OrderDate (Monthly trend)

    Column Chart: Total Sales Quantity by ProductName

    Table: Sales detail (SalesOrderID, OrderDate, ProductName, Quantity, CustomerID)

Page 4: Logistics & Shipments

    Pie Chart: Shipments by Status (Delivered, Processing, Delayed, In Transit)

    Bar Chart: Total Shipments by CarrierID

    Column Chart: Total Shipments by OriginWarehouseID

Page 5: Key Findings & Insights

    Text-based insights and recommendations (no charts)

    Includes: Supplier performance summary, sales patterns, logistics observations, strategic recommendations

KEY NOTES 

    Data Model: Star schema with Supplier_Master as central dimension hub

    3 relationships created: Supplier→PO, Supplier→Performance, PO→POLines

    Shipment_Tracking isolated (data silo - not linked to orders)

    Total records: 250 POs, 1000 Sales Orders, 1000 Shipments, 4 Suppliers

    Date range: 2022-2023 (shows seasonality patterns)
