# Hotel Bar Inventory Forecasting & Par Level Recommendation System (Krystal Ball)

## Overview
This project forecasts daily alcohol consumption across 6 hotel bars using machine learning and statistical models. It calculates dynamic, optimal par stock levels to prevent stockouts while avoiding excessive holding costs. Finally, an inventory policy simulation validates the recommended replenishment strategy under real-world operating conditions.

## Dataset
The dataset consists of **6,575 transaction records** collected between **January 2023 and January 2024**. It covers:
- **6 hotel bars** (Pool Bar, Main Bar, Rooftop, Lobby Lounge, Banquet, Room Service)
- **16 beverage brands**
- **5 alcohol categories** (Beer, Wine, Spirits, Cocktails, Non-Alcoholic)

## Project Structure
```
kristall-ball/
├── data/raw/bar_inventory_data.csv
├── data/processed/daily_bar_consumption.csv
├── notebooks/inventory_forecasting_solution.ipynb
├── report/business_report.md
├── video_script/video_walkthrough_outline.md
├── requirements.txt
└── README.md
```

## How to Run
Follow these simple steps to run the project:

1. **Step 1: Install Python**: Make sure Python 3.9+ is installed.
2. **Step 2: Install Dependencies**: In your terminal, run:
   ```bash
   pip install -r requirements.txt
   ```
3. **Step 3: Open Notebook**: Open `notebooks/inventory_forecasting_solution.ipynb` in Jupyter Notebook or VS Code.
4. **Step 4: Run All Cells**: Execute all cells from top to bottom to run data cleaning, forecasting models, par level optimization, and policy simulations.

## Key Results
- **Best Model**: Random Forest achieved the highest forecast accuracy by effectively capturing day-of-week patterns and weekend demand spikes.
- **Stockout Reduction**: Dynamic par level recommendations significantly reduced stockout risks during peak demand periods.
- **Simulation Validation**: Inventory simulations confirmed that recommended par policies maintain high service levels while lowering average holding inventory.

## Technologies Used
- **Python** (Programming Language)
- **pandas** & **numpy** (Data Processing)
- **matplotlib** & **seaborn** (Visualizations)
- **statsmodels** (Statistical & Time Series Analysis)
- **scikit-learn** (Machine Learning & Modeling)
