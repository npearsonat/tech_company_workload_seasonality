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
3. **Visual Analysis**
  - Visual investigation of key sectors and looking at how the seasonality can be represented by graphing.

## Results / Visualizations

1. Autocorrelation Function
The ACF Graphs of the top 9 seasonality score categories yielded several interesting results. These categories were picked by subtracting the autocorrelation at the 12 month interval by the value at 6 months. This is a short-hand way of determining the companies with the largest difference in 6 month and 12 month revenue, thereby making them good candidates for high seasonality. I then graphed the 1-12 month autocorrelation for these top categories and visually inspected them.

![Visual](visualizations/ACF_comparative.png)

This graph depicts different sectors and the relationship between the revenue they currently generate and how much revenue they have generated in past months. If there is a high autocorrelation in say, company_size = Small in the 12 month range, that means that revenue for a any given month is highly correlated to revenue 12 months ago. Likewise, if the 6 month range has a low autocorrelation, that means that revenue for a given month has a very low correlation to revenue 6 months ago. Highly seasonal categories will have these dips in autocorrelation followed by a rise. 

## Insights / Conclusions

## Dependencies / Requirements

