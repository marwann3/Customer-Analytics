📊 Customer Analytics | Python · Excel · Power BI

An end-to-end analytics project built on a messy dataset of 490,000 customer orders. The raw data was cleaned, enriched and explored with Python and Excel, and delivered as a 3-page interactive Power BI report with a custom landing page, KPI cards and DAX measures.

NTI Data Analytics final project — team: Marwan Mohamed, Mohamed Yasser, Mahmoud Elsaid.

Landing page

🎯 Business Questions
How much order value does the business generate, and from which products, countries and payment methods?
Which customer segments (account balance, satisfaction, premium status) matter most?
How does revenue move across the months?
How satisfied are customers, and does it differ across segments?
📂 Dataset
File: dirty_customer_orders_500k_v2.csv — 490,000 rows × 28 columns (too large for GitHub's 100 MB file limit, so data/ holds a random 5,000-row sample; the full file is available on request)
Fields: customer details (name, email, phone, age, gender, city, country), job data (department, job title, hire date, salary, bonus, performance score), order data (product, quantity, unit price, total amount, order date, status, payment method), plus account balance, satisfaction, premium flag and referral source
Period: orders from January 2018 to December 2025
🛠️ Tools

Python (Pandas, NumPy, Seaborn, Matplotlib) · Excel (data exploration) · Power BI (DAX, bookmarks, custom HTML visual)

🧹 Data Cleaning (Python)

Full code: notebooks/Final_Project1.ipynb. Result: 490,000 → 453,442 rows (7.5% removed as duplicates or invalid records).

Issue	Action
3,754 duplicate customers	Removed
Invalid values	Removed rows with age outside 18–100, performance score above 5 (7,877), negative quantity (4,693), negative unit price (4,666) and satisfaction above 10 (5,771)
Missing numeric values	Median for age, quantity, unit price, performance score and satisfaction; mean for salary, bonus and account balance
Missing categories	Filled with Unknown (gender, city, country, department, job title, product, order status, payment method, referral source, premium flag, phone, email)
Inconsistent text	Trimmed spaces; standardized names, gender, city, country, order status, payment method, referral source and job titles (EG → Egypt, cancel → Cancelled, FB → Facebook...)
Mixed formats	Salary values such as 46392 EGP, $45876, 38,349 and confidential converted to numbers; mixed date formats converted to datetime
Wrong totals	total_amount recalculated as quantity × unit price where it was missing or inconsistent (about 11% of rows)
Outliers	IQR check on account balance found none
⚙️ Feature Engineering

salary_category (quartiles) · balance_category (Debt, Low, Medium, High) · satisfaction_level (Low 0–3, Medium 4–7, High 8–10) · order_year, order_month, order_quarter · tenure_years

📈 Power BI Report
Page	Content
🏠 Home	Custom HTML landing page (driven by a DAX measure) with navigation buttons
💰 Business Overview	KPIs: Total Revenue, Total Customers, Completed Orders %, Avg Satisfaction. Visuals: revenue trend, revenue by product, customers by balance category, revenue by country (treemap)
📊 Detailed Analytics	KPIs: Premium Customers %, Avg Account Balance, Avg Tenure Years, High Satisfaction %. Visuals: satisfaction by month, revenue by balance category, customers by product, satisfaction levels, revenue by payment method, city table

DAX measures: Total Customers, Completed Orders %, Premium Customers %, High Satisfaction %, Landing Page. Both report pages include month and product slicers and page navigation.

Business Overview Detailed Analytics

🔍 Key Insights

Calculated from the full cleaned dataset (453,442 rows).

Scale: 453,442 customers (one order each) with a total order value of 7.33bn. The average order is about 16.2K and the median about 12.4K.
Products are close. Tablet (0.85bn), Monitor (0.85bn), Laptop (0.84bn) and Phone (0.84bn) lead; the other products sit between 0.74bn and 0.76bn.
Egypt is the largest market with 2.04bn (28% of the total). The UAE, the US and Saudi Arabia each contribute about 1.6bn (22%).
High-balance customers drive the business: 301K customers (66% of the base) generate 4.85bn (66% of revenue).
Revenue is steady through the year. Monthly totals stay between 605M (May) and 616M (September), a gap of under 2%.
Satisfaction is average and uniform: the mean is 5.42 out of 10, with 41% Medium, 30% Low and 29% High. It barely changes across months (5.40–5.44) or order statuses.
Premium status shows no uplift: premium and non-premium customers are each about 47% of customers and 47% of revenue.
⚠️ Data Notes
Some report visuals show a selection, not everything: revenue by product shows 4 products and customers by product shows 7 (both out of 10); revenue by balance category counts the same 4 products; the payment method chart shows the top 5 of 7 methods; and the city table shows the top 5 cities. Their percentages and totals refer to what is displayed. The insights above come from the full dataset.
Total Revenue is the sum of all order values, whatever the status. Only about 19.5% of orders (1.43bn) are Completed; Cancelled, Pending, Active and Inactive orders each add roughly the same amount.
City and country are independent in this dataset (for example, Cairo appears under Egypt, the UAE, the US and Saudi Arabia), so city and country results should not be combined.
The distributions in the data are close to uniform, so the value of this project is in the cleaning and reporting pipeline more than in business discoveries.
📁 Repository Structure
customer-analytics-power-bi/
├── README.md
├── dashboard/
│   └── Customer_Analytics.pbix
├── data/
│   └── sample_dirty_customer_orders_5000.csv
├── notebooks/
│   └── Final_Project1.ipynb
├── presentation/
│   └── Customer-Analytics.pptx
└── screenshots/
    ├── dashboard-home.png
    ├── dashboard-business-overview.png
    └── dashboard-detailed-analytics.png
👤 My Contribution
Data cleaning, transformation and exploratory analysis in Python
Data exploration in Excel
Power BI report: 3 pages (landing page, business overview, detailed analytics) with KPI cards, charts, slicers and DAX measures

## Google Drive Files

Raw Dataset:
https://drive.google.com/file/d/1EB4Bvvg6En_enlpp5vNqVtuGtEf5zhbo/view?usp=drive_link

Cleaned Dataset:
https://docs.google.com/spreadsheets/d/1D4AaEljM_WS_yKMcolEUsCZSYP-IRxvE/edit?usp=drive_link&ouid=101089560514863272483&rtpof=true&sd=true

Power BI File:
https://drive.google.com/file/d/1jT1jcRuEUG3d-OPUwIYJYn4bbygsbV3h/view?usp=drive_link

