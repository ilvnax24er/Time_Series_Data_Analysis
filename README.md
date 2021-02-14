# Time_Series_Data_Analysis
Time Series Data Analysis based on Udemy 'Python for Time Series Data Analysis'

# Time Series Analysis with Statsmodel
The <a href='https://en.wikipedia.org/wiki/Hodrick%E2%80%93Prescott_filter'>Hodrick-Prescott filter</a> separates a time-series  ![yt](https://user-images.githubusercontent.com/60414972/107868028-e2f02880-6ec3-11eb-996d-bce1999c7238.jpg) into a trend component ![tau t](https://user-images.githubusercontent.com/60414972/107868035-f602f880-6ec3-11eb-8500-efaa79bc7990.jpg) and a cyclical component ![ct](https://user-images.githubusercontent.com/60414972/107868037-f7ccbc00-6ec3-11eb-8e4d-7621c12ef5ed.jpg)

![yt tau t ct](https://user-images.githubusercontent.com/60414972/107868049-1632b780-6ec4-11eb-8121-7364b0d9480f.jpg)

The components are determined by minimizing the following quadratic loss function, where $\lambda$ is a smoothing parameter:

![formula 1](https://user-images.githubusercontent.com/60414972/107868053-2480d380-6ec4-11eb-9b34-cb05dd4e6416.jpg)


The ![lambda](https://user-images.githubusercontent.com/60414972/107868058-2a76b480-6ec4-11eb-92ea-4445d4ada39b.jpg) value above handles variations in the growth rate of the trend component.<br>When analyzing quarterly data, the default lambda value of 1600 is recommended. Use 6.25 for annual data, and 129,600 for monthly data.
