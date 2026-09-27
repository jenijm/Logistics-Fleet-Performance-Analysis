# Logistics & Fleet Performance Analysis

## 📌 Project Overview

This project analyzes logistics and transportation data to understand fleet performance, delivery efficiency, fuel efficiency, and operating cost.

The dashboard was created using **Microsoft Power BI**.

## 🎯 Objectives

* Analyze on-time delivery performance by route
* Analyze fuel efficiency trends over time
* Calculate cost per kilometer
* Analyze delivery performance geographically
* Build an interactive logistics operations dashboard

## 🛠️ Tools Used

* Microsoft Power BI
* Power Query
* DAX
* Excel

## 📊 Dashboard Pages

### Page 1 — Delivery Performance

* **On-Time Delivery % by Route**
* **Fuel Efficiency Trend by Month**

### Page 2 — Fleet & Cost Analysis

* **Cost per km**
* **Delivery Performance by Route**

## 🔄 Data Cleaning & Transformation

The following data preparation steps were performed using Power Query:

* Removed unnecessary/non-data rows
* Created a unique `Trip_ID`
* Cleaned text fields using Trim/Clean
* Corrected data types
* Checked missing values
* Prepared date fields for analysis
* Created relationships between the trip and vehicle tables

## 🔗 Data Model

The project uses a relationship between:

**Vehicle_Master (1) → Trip_Data (*)**

The relationship is based on `Vehicle_ID`.

## 📐 DAX Measures

### Fuel Efficiency

```DAX
Fuel Efficiency =
DIVIDE(
    SUM(Trip_Data[Distance_km]),
    SUM(Trip_Data[Fuel_Consumed_L])
)
```

### On-Time Delivery %

```DAX
On-Time Delivery % =
DIVIDE(
    CALCULATE(
        COUNTROWS(Trip_Data),
        Trip_Data[Delivery_Status] = "On-Time"
    ),
    COUNTROWS(Trip_Data)
)
```

### Fuel Cost

```DAX
Fuel Cost =
SUM(Trip_Data[Fuel_Consumed_L]) * 100
```

### Cost per km

```DAX
Cost per km =
DIVIDE(
    [Fuel Cost] + SUM(Vehicle_Master[Maintenance_Cost]),
    SUM(Trip_Data[Distance_km])
)
```

## ⚠️ Assumption

The dataset contains fuel consumption in litres but does not provide an actual fuel price.

Therefore, **₹100 per litre** was used as an assumed fuel price for calculating Fuel Cost and Cost per km.

The resulting Cost per km should therefore be interpreted as a calculated estimate based on this assumption, rather than the actual historical fuel cost.

## 📈 Key Dashboard Metrics

* On-Time Delivery %
* Fuel Efficiency
* Cost per km
* Route-level delivery performance
* Monthly fuel efficiency trend

## 📁 Project File

The Power BI report is available in this repository:

`Logistics_Fleet_Performance_Analysis.pbix`

## 👤 Author

**Jeni J Mol**

Data Analytics Project — Power BI
