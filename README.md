# 🛒 DMart Retail Sales Analysis | Python EDA

## 📌 1. Project Overview

This project focuses on Exploratory Data Analysis (EDA) of a simulated Indian retail sales dataset inspired by the supermarket retail industry.

The objective is to analyse retail transactions, understand customer purchasing patterns, evaluate product category performance, examine sales trends and identify factors affecting profitability.

Using Python, I performed data inspection, data cleaning, feature engineering, statistical analysis and data visualization to transform raw transactional data into meaningful business insights.

The project demonstrates a practical Data Analyst workflow, from preparing raw data to exploring business performance through visualizations and analytical summaries.

**Dataset Disclaimer:** This project uses synthetic data generated for educational and portfolio purposes. It does not contain actual DMart transaction records and is not affiliated with DMart.

---

## 🎯 2. Business Objectives

The main objective is to explore retail sales data and understand different aspects of business performance.

The analysis focuses on answering the following business questions:

1. What does the overall sales distribution look like?
2. How are product quantities distributed across transactions?
3. What is the distribution of customers across gender categories?
4. Which product categories have the highest number of records?
5. Which payment methods are most frequently used?
6. Which product categories generate the highest revenue?
7. Which cities contribute the most to total sales?
8. How does revenue vary across customer segments?
9. Which product categories generate the highest profit?
10. Which payment methods contribute the most revenue?
11. How do monthly sales and profit change over time?
12. What relationships exist between numerical variables?
13. Which products generate the highest revenue?
14. Which products contribute the highest profit?
15. What is the average transaction amount across customer segments?

These questions help demonstrate how transactional data can be used to understand sales and profitability.

---

## 📂 3. Dataset Description

The dataset contains approximately 30,000 retail transaction records.

Each record represents a retail transaction containing information about orders, stores, customers, products, pricing and payment methods.

### Dataset Columns

| Column | Description |
|---|---|
| Order_ID | Unique order identifier |
| Order_Date | Date of transaction |
| Store_ID | Store identification number |
| City | City where the transaction occurred |
| State | State associated with the store |
| Customer_ID | Unique customer identifier |
| Gender | Customer gender category |
| Age | Customer age |
| Segment | Customer segment |
| Phone | Customer contact number |
| Product_ID | Product identification number |
| Product_Name | Name of the product |
| Category | Main product category |
| Sub_Category | Product subcategory |
| Quantity | Number of units purchased |
| MRP | Maximum Retail Price |
| Selling_Price | Actual selling price per unit |
| Cost_Price | Cost price per unit |
| Discount | Discount applied |
| Payment_Mode | Payment method used |
| Total_Amount | Total transaction amount |

### Additional Columns Created

During the analysis, two additional columns were created:

- **Month:** Extracted from Order_Date to perform monthly sales and profit analysis.
- **Profit:** Calculated using Selling_Price, Cost_Price and Quantity.

---

## 🛠️ 4. Tools and Technologies

| Tool / Library | Purpose |
|---|---|
| Python | Main programming language |
| Jupyter Notebook | Development environment |
| Pandas | Data manipulation and cleaning |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |
| GitHub | Project documentation and version control |

---

## 🔄 5. Project Workflow

The project follows a structured Data Analytics workflow.

### Step 1: Data Loading and Inspection

The raw CSV dataset was loaded into Python using Pandas.

Initial inspection included:

- Viewing the first and last records.
- Checking the number of rows and columns.
- Reviewing column names.
- Checking data types.
- Generating summary statistics.
- Identifying missing values.
- Checking duplicate records.

### Step 2: Data Cleaning and Preparation

The original dataset contained several data quality issues, including missing values, duplicate records, inconsistent text formatting, invalid numerical values and inconsistent phone number formats.

The following cleaning activities were performed.

**1. Handling Missing Values**

- Identified missing values across all columns.
- Replaced text-based null representations such as `NULL`, `N/A` and blank strings with proper missing values.
- Filled missing categorical values in City, State, Category, Sub_Category and Payment_Mode with `Unknown` where appropriate.
- Retained missing Phone values because the original contact information could not be reliably recovered.
- Used a city-to-state mapping to fill missing State values wherever the city was available.
- Retained unresolved missing locations rather than guessing their values.

**2. Removing Unnecessary Columns**

- Removed the Customer_Name column because Customer_ID was sufficient for customer-level identification.
- This also avoided retaining unnecessary personal information.

**3. Standardizing Text Values**

- Removed leading and trailing spaces.
- Standardized inconsistent capitalization.
- Standardized values in columns such as City, State, Gender, Segment, Category, Sub_Category and Payment_Mode.
- Corrected inconsistent text representations wherever possible.

**4. Handling Duplicate Records**

- Identified duplicate rows using Pandas.
- Removed duplicate records to avoid repeated records affecting the analysis.

**5. Handling Invalid Numerical Values**

- Identified invalid Quantity values, including zero and negative quantities.
- Identified unrealistic Age values, such as values above 100.
- Replaced invalid numerical values with missing values and handled them using median values.

**6. Phone Number Cleaning**

- Removed unnecessary spaces and hyphens.
- Standardized country-code prefixes where possible.
- Retained genuinely missing phone numbers.

**7. Final Validation**

- Checked remaining missing values.
- Verified column names and data types.
- Reviewed the cleaned dataset.
- Exported the cleaned dataset as `dmart_sales_cleaned.csv`.

### Step 3: Feature Engineering

Additional columns were created to support business analysis.

**Month Column**

Extracted month information from Order_Date to analyse monthly sales and profit trends.

**Profit Column**

Profit was calculated using:

`Profit = (Selling_Price - Cost_Price) × Quantity`

This calculation helped evaluate the profitability of products and product categories.

---

## 📊 6. Exploratory Data Analysis (EDA)

EDA was performed using three main approaches: Univariate Analysis, Bivariate Analysis and Multivariate Analysis.

### A. Univariate Analysis

Univariate analysis was used to understand the distribution of individual variables.

The following visualizations were created:

**1. Distribution of Sales**

A histogram was used to understand the distribution of transaction amounts.

Observation:
- Most transactions have relatively low sales amounts.
- The frequency of transactions decreases as sales amounts increase.
- The distribution is positively skewed (right-skewed).

**2. Quantity Distribution**

A count plot was used to understand the frequency of different purchased quantities.

Observation:
- Quantity values are distributed relatively evenly across the recorded values.
- No single quantity value dominates significantly.

**3. Customer Gender Distribution**

A count plot was used to examine the distribution of customer gender categories.

Observation:
- Female, Male and Other categories have relatively similar record counts.
- A smaller number of records belong to the Unknown category.

**4. Product Category Distribution**

A count plot was used to understand the number of records across product categories.

Observation:
- Foods has the highest number of records.
- Non-Foods and General Merchandise & Apparel have different transaction volumes.
- Some records have an Unknown category.

**5. Payment Mode Distribution**

A count plot was used to examine the frequency of different payment methods.

Observation:
- Cash, UPI, Debit Card, Credit Card and Net Banking have relatively similar record counts.
- Some records have an Unknown payment mode.

### B. Bivariate Analysis

Bivariate analysis was performed to understand relationships between two variables.

**6. Sales by Product Category**

A bar chart was used to compare total sales across product categories.

Observation:
- General Merchandise & Apparel generated the highest sales in the initial analysis.
- Foods was the second-highest category.
- Non-Foods generated lower sales compared with the leading categories.

**7. Sales by City**

A bar chart was used to compare total sales across different cities.

Observation:
- Sales were relatively close across several cities.
- Some variation was observed between city-level sales.
- Records with Unknown city information contributed comparatively lower sales.

**8. Sales by Customer Segment**

A bar chart was used to compare sales across Corporate, Wholesale and Retail customer segments.

Observation:
- All three segments generated relatively similar sales.
- No major difference was observed in their total revenue contributions.

**9. Profit by Product Category**

A bar chart was used to compare total profit across product categories.

Observation:
- General Merchandise & Apparel generated significantly higher profit than the other categories.
- Foods and Non-Foods contributed lower total profit.
- Unknown category records also contributed to total profit.

**10. Sales by Payment Mode**

A bar chart was used to compare total revenue across payment methods.

Observation:
- UPI and Cash contributed relatively high sales.
- Other payment methods also generated considerable revenue.
- Unknown payment mode records contributed a smaller share.

### C. Time-Based Analysis

Time-based analysis was performed to understand changes in sales and profitability over time.

**11. Monthly Sales Trend**

A line chart was created to analyse monthly sales performance.

Observation:
- Sales fluctuated across different months.
- Some months recorded higher sales than others.
- Monthly comparisons can help identify periods of stronger and weaker sales performance.

**12. Monthly Profit Trend**

A line chart was created to analyse monthly profit performance.

Observation:
- Profit changed across different months.
- Some periods generated higher profit than others.
- Comparing monthly sales and profit helps understand changes in profitability.

### D. Multivariate Analysis

**13. Correlation Heatmap**

A correlation heatmap was created to understand relationships between numerical variables.

The following variables were included:

- Age
- Quantity
- MRP
- Selling_Price
- Cost_Price
- Discount
- Total_Amount
- Profit

Important observations:

- MRP and Selling_Price showed a very strong positive correlation.
- Selling_Price and Cost_Price also showed a very strong positive correlation.
- Total_Amount and Profit showed a strong positive correlation.
- Quantity and Total_Amount showed a moderate positive correlation.
- Age had almost no linear correlation with Total_Amount.

Correlation indicates association between variables and does not establish causation.

### E. Additional Analytical Summaries

The following summary analyses were also performed using Pandas GroupBy operations.

**14. Top 10 Products by Sales**

Identified the ten products generating the highest total sales.

**15. Top 10 Products by Profit**

Identified the ten products contributing the highest total profit.

**16. Average Sales by Customer Segment**

Calculated average transaction sales for each customer segment to compare their average sales values.

---

## 📌 7. Key Findings and Business Observations

Based on the initial EDA, the following observations were identified:

| Analysis Area | Observation |
|---|---|
| Sales Distribution | Sales transactions showed a right-skewed distribution. |
| Quantity | Recorded quantities were relatively evenly distributed. |
| Gender | Male, Female and Other categories had similar record counts. |
| Product Category | Foods had the highest number of records. |
| Category Revenue | General Merchandise & Apparel generated the highest sales. |
| City Performance | Several cities showed relatively similar sales contributions. |
| Customer Segment | Corporate, Wholesale and Retail generated similar total sales. |
| Category Profitability | General Merchandise & Apparel generated the highest total profit. |
| Payment Mode | UPI and Cash contributed relatively high sales. |
| Monthly Performance | Sales and profit fluctuated across different months. |
| Correlation | Selling_Price and MRP had a very strong positive relationship. |

These findings provide an initial understanding of the dataset and help identify areas for further analysis.

---

## 💡 8. Business Value

This project demonstrates how retail transaction data can be used to understand business performance.

The analysis can help investigate:

- Which product categories generate the most revenue.
- Which categories contribute the highest profit.
- How sales performance differs across cities.
- How customer segments contribute to revenue.
- Which payment methods account for higher sales.
- How sales and profit change over time.
- Which products contribute significantly to sales and profitability.

These observations can support further investigation into product performance, pricing strategies and retail sales opportunities.

---

## Project Work Flow/Structure 
```text
DMart-eda-pyhton-Analysis/
│
├── Dataset/
│   ├── dmart_sales_cleaned.csv
│   └── dmart_sales_text_messy.csv
│
├── Notebooks/
│   ├── DMart_EDA.ipynb
│   └── Dmart_datacleaning.ipynb
│
└── README.md
```




