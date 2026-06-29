# AI Business Report Generator

An end-to-end business analytics dashboard that turns CSV sales data into KPIs, trend analysis, structured insights, and AI-generated executive reports using Python, Streamlit, Pandas, and a local Ollama model.

## Project Overview

This project simulates a practical business reporting workflow. A user can upload a CSV file, map the dataset columns, filter the data, view business KPIs and charts, generate structured insights, and create an executive-style AI report.

The project is designed for business analyst, data analyst, and AI application portfolio use cases. It shows how traditional data analysis can be combined with local LLM-based report generation.

## What This Project Does

- Loads CSV sales or business data
- Cleans and prepares the dataset
- Automatically suggests column mappings for different CSV formats
- Lets the user manually map columns when needed
- Calculates business KPIs
- Analyzes revenue by category and region
- Generates weekly and monthly revenue trends
- Creates structured business insights
- Sends the insights to a local Ollama LLM
- Generates executive-style business reports
- Supports multiple report styles
- Provides a fallback template report if Ollama is unavailable
- Displays results in an interactive Streamlit dashboard
- Allows report and filtered data downloads

## Key Features

### General CSV Support

The app is no longer limited to one fixed dataset format. It can work with different CSV files by mapping available columns to the fields needed for analysis.

The app tries to automatically identify:

- Date column
- Revenue or sales column
- Profit column
- Region/location column
- Category/product column

For example, one dataset may use:

```text
Order Date, Sales, Profit, Region, Category
```

Another dataset may use:

```text
Order Date, Sales, City, Product
```

The sidebar allows the user to confirm or change the mapping before analysis.

### Dashboard Filters

The dashboard supports:

- Date range filtering
- Region/location filtering
- Category/product filtering
- Uploaded CSV files
- Default local dataset

### KPI Analysis

The app calculates:

- Total revenue
- Total profit
- Total orders
- Average order value
- Weekly revenue trend
- Monthly revenue trend
- Weekly and monthly growth/decline rates

### Visual Analysis

The Streamlit dashboard includes:

- KPI cards
- Revenue by category chart
- Revenue by region chart
- Weekly revenue trend chart
- Monthly revenue trend chart
- Detailed filtered data preview
- Detailed analysis tables

### AI Executive Report Generation

The app converts structured insights into a professional report using a local Ollama model.

Default model:

```text
llama3.2:1b
```

The user can choose the report style:

- Executive Summary
- Sales Manager Report
- Risk Analysis Report
- Action Plan Report

### Fallback Report Mode

If Ollama is not running or the model is unavailable, the app can still generate a template-based report using the structured insights. This makes the project easier to demo and more reliable.

### Automatic Output Folder Creation

The app automatically creates the `outputs` folder before saving the generated report. This prevents file save errors when running the project for the first time.

## Tech Stack

- Python
- Pandas
- NumPy
- Streamlit
- Requests
- Ollama
- Local LLM: `llama3.2:1b`

## Project Structure

```text
ai-business-report-generator-main/
|-- app/
|   |-- streamlit_app.py
|
|-- data/
|   |-- superstore_sales.csv
|
|-- outputs/
|   |-- business_report.txt
|
|-- src/
|   |-- analysis.py
|   |-- data_cleaning.py
|   |-- data_loader.py
|   |-- insight_engine.py
|   |-- llm_report.py
|
|-- main.py
|-- README.md
|-- requirements.txt
```

## How The Pipeline Works

```text
CSV Data
  -> Data Loading
  -> Data Cleaning
  -> Column Mapping
  -> KPI Calculation
  -> Category and Region Analysis
  -> Weekly and Monthly Trend Analysis
  -> Structured Business Insights
  -> AI or Fallback Report Generation
  -> Streamlit Dashboard
  -> Downloadable Report
```

## Column Mapping Logic

The app uses both column names and data patterns to guess the correct fields.

Examples:

- Columns containing `date`, `order_date`, or `invoice_date` are treated as date candidates.
- Columns containing `sales`, `revenue`, `amount`, or `price` are treated as sales candidates.
- Columns containing `profit`, `margin`, or `income` are treated as profit candidates.
- Columns containing `region`, `state`, `country`, `city`, or `market` are treated as region/location candidates.
- Columns containing `category`, `product`, `segment`, or `department` are treated as category/product candidates.

The app also checks whether values look like dates, numbers, or repeated text groups.

## Example Dataset Mapping

For the default `superstore_sales.csv` dataset:

```text
Date column: Order Date
Revenue or sales column: Sales
Profit column: Profit
Region column: Region
Category column: Category
```

For a general sales dataset like `Sales Data.csv`:

```text
Date column: Order Date
Revenue or sales column: Sales
Profit column: Not available
Region column: City
Category column: Product
```

If profit is not available, the app fills profit as `0` so the rest of the analysis can still run.

## Why Ollama Is Used

This project uses Ollama instead of a paid cloud API because:

- No API key is required
- No subscription is required
- The model runs locally
- It is easier to demo as a portfolio project
- Business data does not need to be sent to an external API
- It demonstrates local LLM integration

## Requirements

Install Python 3.10 or newer.

Install project dependencies:

```powershell
pip install -r requirements.txt
```

Install Ollama from:

```text
https://ollama.com
```

Pull the local model:

```powershell
ollama pull llama3.2:1b
```

Check installed models:

```powershell
ollama list
```

## How To Run The Project

Open PowerShell in the project folder:

```powershell
cd "C:\Users\monst\OneDrive\Desktop\Proj\Report Generator\ai-business-report-generator-main"
```

Create a virtual environment:

```powershell
python -m venv .venv
```

Activate the virtual environment:

```powershell
.venv\Scripts\activate
```

Install dependencies:

```powershell
pip install -r requirements.txt
```

Run the Streamlit app:

```powershell
streamlit run app\streamlit_app.py
```

Open the local Streamlit URL shown in the terminal, usually:

```text
http://localhost:8501
```

## How To Generate An AI Report

1. Start the Streamlit app.
2. Upload a CSV file or use the default dataset.
3. Check the column mapping in the sidebar.
4. Adjust mappings if needed.
5. Apply filters if needed.
6. Select a report style.
7. Click `Generate AI Report`.
8. Download the generated report.

## If Ollama Is Not Working

Check whether Ollama is running:

```powershell
ollama list
```

If the model is missing:

```powershell
ollama pull llama3.2:1b
```

If Ollama still fails, the app will create a fallback template-based report instead.

## Skills Demonstrated

- Python programming
- Data loading and cleaning
- CSV handling
- Data analysis with Pandas
- KPI calculation
- Time-series trend analysis
- Business insight generation
- Streamlit dashboard development
- Dynamic column mapping
- Local LLM integration with Ollama
- Prompt engineering
- Error handling and fallback logic
- Downloadable report generation
- Portfolio-ready analytics application design


## Future Improvements

- Add PDF report export
- Add automatic chart recommendations
- Add comparison mode for current vs previous period
- Add more advanced anomaly detection
- Add support for Excel files
- Add authentication for business users
- Add dashboard theme customization
