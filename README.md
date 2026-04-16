📊 Data Modeler – Star Schema Data Modeling in Power BI
🔹 Project Overview
This project focuses on building a well-structured data model in Power BI using multiple normalized tables. The objective is to design an efficient Star Schema, define relationships, and validate data flow without using DAX or calculated columns.

🎯 Objective
Design a Star Schema data model
Define Primary Key (PK) and Foreign Key (FK) relationships
Apply correct cardinality and filter direction
Handle inactive relationships and ambiguity
Create hierarchies for better navigation
Validate model using Matrix visuals
📂 Dataset Description
📊 Fact Tables
Sales_Fact

SalesID (PK)
CustomerID, ProductID, RegionID, DateKey (FKs)
Quantity, Revenue, Discount
Returns_Fact

ReturnID (PK)
SalesID (FK)
ReturnDateKey (FK)
Reason
📁 Dimension Tables
Customer_Dim → Customer details (Segment, Gender, Age)
Product_Dim → Product details (Category, Subcategory, Brand)
Region_Dim → Location (Country, State, City)
Date_Dim → Time (Year, Quarter, Month, Fiscal Year)
🔄 Data Preparation (Power Query)
Imported all datasets using Excel connector

Removed null and duplicate rows

Renamed columns for consistency

Assigned appropriate data types

IDs → Whole Number
Revenue → Decimal
Date → Date format
🧠 Data Modeling Approach
⭐ Schema Design
Implemented a Star Schema
Sales_Fact used as central table
Returns_Fact modeled as a secondary fact table (Fact Constellation)
🔗 Relationships
From Table	To Table	Type
Sales → Customer	Many-to-One	
Sales → Product	Many-to-One	
Sales → Region	Many-to-One	
Sales → Date	Many-to-One	
Returns → Sales	Many-to-One	
Returns → Date	Inactive	
⚙️ Cardinality & Filter Direction
Used Many-to-One relationships
Applied Single Direction filtering to avoid ambiguity
❗ Inactive Relationship
Returns_Fact → Date_Dim (ReturnDateKey) set as Inactive
Prevents multiple active filter paths and ambiguity
🧱 Data Model Enhancements
Hierarchies
Date: Year → Quarter → Month → Date
Region: Country → State → City
Product: Category → Subcategory → ProductName
Data Formatting
Revenue → Currency
Quantity → Whole Number
Date → Standard Date format
📊 Model Validation (Matrix Visuals)
The following matrices were used to validate relationships:

Category vs Country → Electronics revenue: 102,893, USA contribution: 44,712

Return Reason vs Fiscal Year → Total returns: 100, highest: Not Needed (35)

Year vs Revenue → 2022: 138,376 → 2023: 148,550

Segment vs Revenue → Silver segment highest: 97,436

Country vs Year → USA total: 124,162, Overall revenue: 286,926

👉 These validate correct filter propagation and aggregation

⚠️ Challenges & Solutions
Ambiguity Issue

Multiple paths between tables ✔️ Resolved using single-direction filters + inactive relationship
Data Consistency

Different formats across files ✔️ Cleaned and standardized using Power Query
📚 Key Learnings
Star Schema design principles
Relationship cardinality (1:M)
Handling inactive relationships
Avoiding filter ambiguity
Building scalable data models
✅ Conclusion
This project demonstrates a robust and scalable Power BI data model using best practices in data modeling. The use of star schema, proper relationships, and validation techniques ensures accurate and efficient data analysis.
