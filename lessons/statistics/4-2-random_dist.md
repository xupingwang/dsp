[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

>> 
pmf = thinkstats2.Pmf(np.random.random(1000), label='random_number probability distribution')
thinkplot.Hist(pmf)
thinkplot.Config(xlabel='random_number', ylabel='probability')
#the problem with pmf function is that as the amount of random number increases, the probability density diminishes.

cdf = thinkstats2.Cdf(np.random.random(1000), label='cdf')
thinkplot.Cdf(cdf)
thinkplot.Config(xlabel='random_number', ylabel='cumulative probability distribution', loc='upper left')
