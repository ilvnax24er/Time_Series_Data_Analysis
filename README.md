# Time_Series_Data_Analysis
Time Series Data Analysis based on Udemy 'Python for Time Series Data Analysis'

# Time Series Analysis with Statsmodel
The <a href='https://en.wikipedia.org/wiki/Hodrick%E2%80%93Prescott_filter'>Hodrick-Prescott filter</a> separates a time-series  ![yt](https://user-images.githubusercontent.com/60414972/107868028-e2f02880-6ec3-11eb-996d-bce1999c7238.jpg) into a trend component ![tau t](https://user-images.githubusercontent.com/60414972/107868035-f602f880-6ec3-11eb-8500-efaa79bc7990.jpg) and a cyclical component ![ct](https://user-images.githubusercontent.com/60414972/107868037-f7ccbc00-6ec3-11eb-8e4d-7621c12ef5ed.jpg)

$y_t = \tau_t + c_t$

The components are determined by minimizing the following quadratic loss function, where $\lambda$ is a smoothing parameter:

$\min_{\\{ \tau_{t}\\} }\sum_{t=1}^{T}c_{t}^{2}+\lambda\sum_{t=1}^{T}\left[\left(\tau_{t}-\tau_{t-1}\right)-\left(\tau_{t-1}-\tau_{t-2}\right)\right]^{2}$


The $\lambda$ value above handles variations in the growth rate of the trend component.<br>When analyzing quarterly data, the default lambda value of 1600 is recommended. Use 6.25 for annual data, and 129,600 for monthly data.
