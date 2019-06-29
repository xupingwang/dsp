[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>> 
from scipy.stats import norm
average_height = 178
std = 7.7
lower_limit = 177.80
upper_limit = 185.42
std_upper = (upper_limit - average_height) / std
std_lower = (lower_limit - average_height) / std
print(norm.cdf(std_upper) - norm.cdf(std_lower))

#Answer: only 34.27% of U.S. male is in the height range of Blue Man Group
