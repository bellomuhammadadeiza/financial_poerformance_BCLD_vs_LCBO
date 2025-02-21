# Project Overview
This project compares the financial performance of BCLDB and LCBO using publicly available financial reports. It involves data extraction, cleaning, analysis, and dashboard visualization to highlight key insights.
## 1. Companies Overview
### 1.1 BCLDB Overview
The British Columbia Liquor Distribution Branch (BCLDB) is a government-owned entity responsible for the wholesale distribution, the retail sale of alcoholic beverages, and regulating other private retailers in British Columbia. It operates under the provincial Ministry of Finance. Its management structure is strictly controlled by the provincial government. 
### 1.2 LCBO Overview
The Liquor Control Board of Ontario (LCBO) is a Crown corporation owned by the Ontario government. Unlike the BCLDB, the LCBO operates with greater autonomy and functions as a self-sustaining enterprise with its own board of directors.
## 2. Data Collection
### Data Sources
- For BCLDB, the financial data was sourced from BCLDB annual reports for fiscal years 2018-2019 through 2023-2024 available at https://www.bcldb.com/publications/annual-report, downloaded as PDF. 
- For LCBO, the financial data was sourced from LCBO annual reports for fiscal years 2018-2019 through 2023-2024 available at https://www.lcbo.com/content/lcbo/en/corporate-pages/about/annual-report-business-plan-intro.html?srsltid=AfmBOor2Lyn8VQaMGMpQUVGcntO8LjIAy95krFrDekzjz0TD0IAhkE5k
### Data Extraction
I used the (```Tabula```) in Python to extract the financial statements from the annual reports and then save each statement in CSV format. Using the code below:
  
  ```
  from tabula import read_pdf
  pdf_path = "filename.pdf"
  # Extract tables from all pages
  tables = read_pdf(pdf_path, pages="all", multiple_tables=True)
  # Save each extracted table as CSV files
  for i, table in enumerate(tables):
      csv_filename = f"BCLDB_Table_{i+1}.csv"
      table.to_csv(csv_filename, index=False)
      print(f"Table {i+1} saved as {csv_filename}")
  
  ```
 ### Data Cleaning
The extracted data were merged in one CSV file, cleaned and validated in Excel
 
## Exploratory Analysis
- This was done using Pivot Table in Excel.
- The financial ratios were calculated via automation using ```calculated items``` under ```Fields, Items & Sets```
- After calculating all the ratios, ```slicer``` was inserted for company comparison and ```timeline``` for yearly trends
- On separate worksheets, the YoY performance/trends of the financial metrics were visualized using the ```line chart``` of the ```pivot chart```, and chart formatting/design was done appropriately using ```chart design```
- On another worksheet, I created a professional interactive dashboard using the chats and calculated metrics
- missing data/error ```#DIV/0 Error``` was controlled for using the ```IFFERROR``` function in excel

![LCBO Financial performance Dashboard](images/lcbo_dashboard.png) <p align="center"><sub>Figure 1: LCBO financial performance dashboard</sub></p>

![BCLDB Financial performance Dashboard](images/bcldb_dashboard.png) <p align="center"><sub>Figure 2: BCLDB financial performance dashboard</sub></p>

![BCLDB & LCBO Financial performance Dashboard](images/bcldb_lcbo_display.gif)

The work file for this project in Excel is available for d [Download Excel Work File](excel/bcldb_lcbo_financial_analysis.xlsx)


