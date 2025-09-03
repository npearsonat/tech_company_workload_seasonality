# Tech Company Workload Seasonality
Analysis for a tech company partnered with Northeastern University during the spring quarter of 2025. The data was anonomyzed, and I have provided a sample of the first 100 rows in the data section of this project, but it will unfortunately not be reproducable. This tech company requested that we analyze their billing data and report any interesting patterns and occurences we can. 

## Motivation / Purpose
The client listed a few things they wanted from us, including predictions, trends and revenue statistics. I chose to focus on the identification of seasonal patterns related to their workload and specific clients or groups of clients.

## Data

One excel file including the columns:
- **Customer Name**: Name of customer where they performed the work
- **Project**: Name of project.
- **Worked Date**: Date of time of entry for the work.
- **Task or Ticket Title**: Title of task or ticket.
- **Resource Name**: Person on their team who delivered the project.
- **Billable Hours**: Number of hours worked for the customer. 
- **Billing Rate**: Rate for consultant on that role on that project
- **Extended Price**: Number of hours multiplied by rate. 

## Methods / Approach

1. **Feature Engineering**: Created customer_category column to sort customers into different sectors. Created multiple columns sorting projects into categories like small/medium/large, days since last project, project category, etc.
2. **Statistical Analysis**:
    - **Autocorrelation Function ACF** captures similarity between a time series and a lagged version of itself over successive intervals time intervals. It calculates the correlation between two different versions of the same time series.

![Visual](visualizations/autocorrelation_function.png)
- Cov is covariance, σ is standard deviation, Xt represents variable at time t

    - **Seasonality Score** calculates ACF for series and returns correlation at lag 12, lag 6, and lag 4. Symbolizing an annual pattern, semi-annually and quarterly patterns.
    - **Seasonal Decomposition** It splits a time series into three components:
          - Trend – the long-term increase or decrease.
          - Seasonal – the repeating pattern within each period (e.g., months of a year).
          - Residual – what’s left over after removing trend and seasonality (noise or irregular fluctuations).
      The seasonal component is then graphed.
      -**Fourier Transformation** detrends the monthly revenue, converts the time series from the time domain to frequency domain, breaks revenue into waves, and tells you which waves dominate
3. **ACF Graphing**
  - Visual investigation of key sectors 

## Results / Visualizations

## Insights / Conclusions

## Dependencies / Requirements

