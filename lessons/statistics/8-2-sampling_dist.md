[Think Stats Chapter 8 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77) (scoring)

>> 

def SimulateSample(lam = 2, n=10, iters=1000):
    xbars = []
    for j in range(iters):
        xs = np.random.exponential(1.0/lam, n)
        xbar = np.mean(xs)
        xbars.append(xbar)
    return xbars

xbars = SimulateSample()

cdf = thinkstats2.Cdf(xbars)
thinkplot.Cdf(cdf)
thinkplot.Config(xlabel='Sample mean',
                 ylabel='CDF')

print("sample mean is: " + str(np.mean(xbars)))

stderr = RMSE(xbars, np.mean(xbars))
print("standard error is: " + str(stderr))

ci = cdf.Percentile(5), cdf.Percentile(95)
print(ci)




import matplotlib.pyplot as plt
def Estimate4(n):
    iters=1000
    lam = 2

    means = []
    medians = []
    for _ in range(iters):
        xs = np.random.exponential(1.0/lam, n)
        L = 1 / np.mean(xs)
        Lm = np.log(2) / thinkstats2.Median(xs)
        means.append(L)
        medians.append(Lm)
    return [n, RMSE(means, lam)]

data = []
for n in range (5, 15):
    data.append(Estimate4(n))
print(data)
    
x_val = [x[0] for x in data]
y_val = [x[1] for x in data]

plt.xlabel('n')
plt.ylabel('standard error')
plt.plot(x_val,y_val)
plt.plot(x_val,y_val,'or')
plt.show()
