# Time-Series-Analysis-for-Transportation
![Baseball Flights](./Images/baseball_flights.png)

Time Series Analysis for Transportation
Explore transportation time series data analysis to uncover patterns and forecast travel costs.

## Project Description
Unlock the value of transportation time series data with a journey into scheduling analysis.

Embark on a data-driven expedition as you delve into the world of transportation time series analysis, focusing on the dynamic scheduling challenges of professional sports. From uncovering flight patterns to utilizing forecasting technologies to estimate travel costs!

## Project Summary

### Goal and Achievement
The primary goal of this project was to analyze the flight schedules for the 2102 season to help The League optimize its transportation logistics. This involved two key objectives:
1.  Determine the maximum number of jets required to service all teams simultaneously.
2.  Forecast the total fuel expenditure for the entire 2102 season.

Through the analysis, we successfully determined that a **maximum of 19 jets** are needed at any single point in time. Furthermore, by forecasting fuel prices, we estimated the **total fuel cost for the season to be approximately $1,859,925**.

### Methodology
The analysis was performed in Python using the following approach:

1.  **Maximum Concurrent Flights:**
    *   All departure and landing timestamps were collected and sorted to create a continuous timeline of events.
    *   A counter was implemented to track the number of teams "in flight" between each consecutive event timestamp.
    *   The results were visualized in a step plot to clearly show the number of simultaneous flights over the season, from which the peak was identified.

2.  **Fuel Cost Forecasting:**
    *   A **Seasonal ARIMA (SARIMAX)** model was trained on the historical fuel price data from the 2101 season. The model was configured with `order=(1, 1, 1)` to handle the data's trend and `seasonal_order=(1, 0, 0, 7)` to capture the weekly seasonality.
    *   This model was used to forecast the daily jet fuel prices for the upcoming 2102 season.
    *   The forecasted prices were then applied to the 2102 flight schedule. The total fuel cost was calculated by determining the fuel needed for each flight (assuming 1 gallon per mile) and multiplying it by the forecasted price for the departure date.

### Key Learnings
This project provided valuable hands-on experience in:
-   **Time-Series Analysis:** Analyzing time-stamped data to identify patterns and peaks, such as concurrent events.
-   **Forecasting:** Applying statistical models like SARIMAX to predict future values based on historical data.
-   **Data Manipulation:** Using the `pandas` library for cleaning, transforming, and merging different datasets.
-   **Data Visualization:** Creating informative plots with `matplotlib` to present findings effectively.

### Technical Requirements
To reproduce the results of this analysis, you will need:
-   **Python 3**
-   The following Python libraries and their core functions:
    -   **pandas**: `read_csv()`, `to_datetime()`, `concat()`, `DataFrame()`, `join()`
    -   **statsmodels**: `tsa.statespace.sarimax.SARIMAX()`
    -   **matplotlib**: `pyplot.subplots()`, `pyplot.show()`, `ax.step()`, `ax.scatter()`
    -   **numpy**

### Installation
To install all the required libraries, run the following command in your terminal:
```bash
pip install -r requirements.txt
```

---
## Original Project Instructions

To the Office of Transportation at The 22nd Century Sporting League,

After our inaugural 2101 season, The League is looking for ways to optimize our game scheduling process and costs.  We know that transportation logistics are a major variable to consider during scheduling, and as such, we’ve got a few questions for you. 

Our primary areas of focus are surrounding the number of jets that The League needs to own, and the cost of fuel for those flights. If we want The League to enjoy continued success, we'll need to make sure we manage transportation costs.

We’re sharing schedule data for the upcoming 2102 season.  On each row, you’ll find information about which teams are needing to travel to their next set of games, the time the flight will likely depart (based on our estimations of gameplay durations) and the time the flight will likely land. 

Additionally, we're also providing the fuel price that was paid each day during this past 2101 season. The fuel price fluctuates over time, but we're hoping you'll be able to project it to the future to help with the analysis.

## The Data

### team_flights.csv

| Column     | Description              |
|------------|--------------------------|
| `team_name` | Official team name |
| `departure_datetime` | Date and Time (in UTC) when the flight will depart |
| `landing_datetime` | Date and Time (in UTC) when the flight will land |


### fuel_price.csv

| Column     | Description              |
|------------|--------------------------|
| `date` | Date when the fuel price was recorded |
| `fuel_price` | Corresponding fuel price (in $ per gallon) |


### Important Things to Know
- You can assume that the flight's average speed is 500 MPH. (So, as an example, a 2-hour flight would travel 1000 miles)
- You can assume that each team’s jet fills up with fuel equivalent to 1 gallon per mile-of-travel 
- You can assume that the jet is fueled on the day the travel departs (and thus can use the fuel price corresponding to the departure date)