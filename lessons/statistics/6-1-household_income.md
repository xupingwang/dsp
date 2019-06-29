[Think Stats Chapter 6 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2007.html#toc60) (household income)

print("median household income is: " + str(np.median(sample)))
print("mean household income is :" + str(sample.mean()))
print(Skewness(sample), PearsonMedianSkewness(sample))
#print(type(cdf))
print("the precentage of household that report a taxable income below the mean is: " + str(100* cdf[sample.mean()]) + "%")

#Answer: as upper bound increases, the median of sample remains, while the mean of sample increases, which causes the skewness coefficient to increase as a result, Vice Versa.
