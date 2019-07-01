[Think Stats Chapter 8 Exercise 3](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77)

---

>> 
def RMSE(estimates, actual):
    """Computes the root mean squared error of a sequence of estimates.

    estimate: sequence of numbers
    actual: actual value

    returns: float RMSE
    """
    e2 = [(estimate-actual)**2 for estimate in estimates]
    mse = np.mean(e2)
    return np.sqrt(mse)
    
def Estimate2(lam):
    iters= 1000
    sigma = 1

    estimates1 = []
    estimates2 = []
    for _ in range(iters):
        xs = [SimulateGame(lam) for i in range(n)]
        xbar = np.mean(xs)

    print('mean error: ', xbar - lam)
    print('root mean square error: ', RMSE(xs, lam))
    
Estimate2(5)
#this estimate is biased
