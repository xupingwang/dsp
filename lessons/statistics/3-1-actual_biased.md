[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

>> 

resp = nsfg.ReadFemResp()
kids_number_house = resp[resp.numkdhh != 0].numkdhh
pmf = thinkstats2.Pmf(kids_number_house, label='actual')

def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)
    for x, p in pmf.Items():
        new_pmf.Mult(x, x)       
    new_pmf.Normalize()
    return new_pmf

biased_pmf = BiasPmf(pmf, label='observed')
thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biased_pmf])
thinkplot.Config(xlabel='Kids per household', ylabel='PMF')

print("The unbiased mean for number of kids per household is: " + str(pmf.Mean()) + ", the unbiased mean is: " +  str(biased_pmf.Mean()))
