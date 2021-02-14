# Time_Series_Data_Analysis
Time Series Data Analysis based on Udemy 'Python for Time Series Data Analysis'

# Time Series Analysis with Statsmodel
The <a href='https://en.wikipedia.org/wiki/Hodrick%E2%80%93Prescott_filter'>Hodrick-Prescott filter</a> separates a time-series  ![yt](https://user-images.githubusercontent.com/60414972/107868028-e2f02880-6ec3-11eb-996d-bce1999c7238.jpg) into a trend component ![tau t](https://user-images.githubusercontent.com/60414972/107868035-f602f880-6ec3-11eb-8500-efaa79bc7990.jpg) and a cyclical component ![ct](https://user-images.githubusercontent.com/60414972/107868037-f7ccbc00-6ec3-11eb-8e4d-7621c12ef5ed.jpg)

![yt tau t ct](https://user-images.githubusercontent.com/60414972/107868049-1632b780-6ec4-11eb-8121-7364b0d9480f.jpg)

The components are determined by minimizing the following quadratic loss function, where $\lambda$ is a smoothing parameter:

![formula 1](https://user-images.githubusercontent.com/60414972/107868053-2480d380-6ec4-11eb-9b34-cb05dd4e6416.jpg)


The ![lambda](https://user-images.githubusercontent.com/60414972/107868058-2a76b480-6ec4-11eb-92ea-4445d4ada39b.jpg) value above handles variations in the growth rate of the trend component.<br>When analyzing quarterly data, the default lambda value of 1600 is recommended. Use 6.25 for annual data, and 129,600 for monthly data.

## Seasonal Decomposition
Statsmodels provides a <em>seasonal decomposition</em> tool we can use to separate out the different components. This lets us see quickly and visually what each component contributes to the overall behavior.


We apply an <strong>additive</strong> model when it seems that the trend is more linear and the seasonality and trend components seem to be constant over time (e.g. every year we add 10,000 passengers).<br>
A <strong>multiplicative</strong> model is more appropriate when we are increasing (or decreasing) at a non-linear rate (e.g. each year we double the amount of passengers).

For these examples we'll use the International Airline Passengers dataset, which gives monthly totals in thousands from January 1949 to December 1960.

___
# EWMA
## Exponentially Weighted Moving Average 

We just showed how to calculate the SMA based on some window. However, basic SMA has some weaknesses:
* Smaller windows will lead to more noise, rather than signal
* It will always lag by the size of the window
* It will never reach to full peak or valley of the data due to the averaging.
* Does not really inform you about possible future behavior, all it really does is describe trends in your data.
* Extreme historical values can skew your SMA significantly

To help fix some of these issues, we can use an <a href='https://en.wikipedia.org/wiki/Exponential_smoothing'>EWMA (Exponentially weighted moving average)</a>.

EWMA will allow us to reduce the lag effect from SMA and it will put more weight on values that occured more recently (by applying more weight to the more recent values, thus the name). The amount of weight applied to the most recent values will depend on the actual parameters used in the EWMA and the number of periods given a window size.
[Full details on Mathematics behind this can be found here](http://pandas.pydata.org/pandas-docs/stable/user_guide/computation.html#exponentially-weighted-windows).
Here is the shorter version of the explanation behind EWMA.

The formula for EWMA is:
### $y_t =   \frac{\sum\limits_{i=0}^t w_i x_{t-i}}{\sum\limits_{i=0}^t w_i}$
