[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

>> 
import first

live, firsts, others = first.MakeFrames()
live = live.dropna(subset=['agepreg', 'totalwgt_lb'])

agepreg, totalwgt_lb = live.agepreg, live.totalwgt_lb

thinkplot.Scatter(agepreg, totalwgt_lb, alpha=0.1, s=10)
thinkplot.Config(xlabel='agepreg',
                 ylabel='totalwgt_lb',
                 axis=[8, 60, 0, 18],
                 legend=False)
                 
bins = np.arange(8, 60, 1)
indices = np.digitize(agepreg, bins)
groups = live.groupby(indices)

for i, group in groups:
    print(i, len(group))
    
mean_agepreg = [group.agepreg.mean() for i, group in groups]
cdfs = [thinkstats2.Cdf(group.totalwgt_lb) for i, group in groups]

for percent in [75, 50, 25]:
    weight_percentiles = [cdf.Percentile(percent) for cdf in cdfs]
    label = '%dth' % percent
    thinkplot.Plot(mean_agepreg, weight_percentiles, label=label)
    
thinkplot.Config(xlabel='agepreg',
                 ylabel='totalwgt_lb',
                 axis=[8, 60, 0, 18],
                 legend=False)
  
print("Pearson's correlation is: " + str(np.corrcoef(agepreg, totalwgt_lb)))

def SpearmanCorr(xs, ys):
    xs = pd.Series(xs)
    ys = pd.Series(ys)
    return xs.corr(ys, method='spearman')

print("Spearman's correlation is: " + str(SpearmanCorr(agepreg, totalwgt_lb)))
#Answer: there are no relationship between agepreg and totalwgt_lb
