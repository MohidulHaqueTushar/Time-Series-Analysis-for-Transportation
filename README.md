# Time-Series-Analysis-for-Transportation
![Baseball Flights](./Images/baseball_flights.png)

## Project Overview
In this project, I analyzed the transportation logistics for a professional sports league's 2102 season. My primary objectives were to determine the optimal number of jets the league needs to own and to forecast the total fuel costs for the season. By analyzing flight schedules and historical fuel prices, I provided data-driven insights to help optimize operational costs.

## Key Results
- **Maximum Required Jets:** I determined that a maximum of **19** jets are required to be in service simultaneously during the season.
- **Forecasted Fuel Cost:** I estimated the total fuel expenditure for the 2102 season to be approximately **$1,859,925**.

## Methodology
I conducted the analysis in a Jupyter Notebook (`Notebooks/notebook.ipynb`) and my approach involved two main parts:

1.  **Concurrent Flight Analysis:** I created a timeline of all flight events to calculate the number of teams in the air at any given moment. I then visualized this to identify the peak demand for jets.
2.  **Fuel Cost Forecasting:** I trained a SARIMAX model on the 2101 fuel price data to forecast prices for the 2102 season, capturing trends and weekly seasonality. I then used these forecasted prices to calculate the total fuel cost for all scheduled flights.

## Getting Started

### Prerequisites
- Python 3

### Installation
1. Clone the repository.
2. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```
3. Explore my analysis in the Jupyter Notebook:
   ```bash
   jupyter notebook Notebooks/notebook.ipynb
   ```

## Data
The analysis uses two datasets provided in the `Datasets/` directory:
- `team_flights.csv`: Contains the flight schedules for each team for the 2102 season.
- `fuel_prices_2101.csv`: Contains the daily fuel prices for the 2101 season.
