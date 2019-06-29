#[Think Stats Chapter 2 Exercise 4] (Cohen's d)


# Solution goes here
firsts = live[live.birthord == 1]
others = live[live.birthord != 1]
first_weight = firsts.totalwgt_lb.mean()
others_weight = others.totalwgt_lb.mean()
print("first babies average weight is: " + str(first_baby_mean_weight) + " lbs, other babies average weight is: "
      + str(others_weight) + " lbs.")
#first Babies are lighter than other babies


print("Cohen's effect size for pregnancy length is :" + str(CohenEffectSize(firsts.prglngth, others.prglngth)))
print("Cohen's effect size for weight is :" + str(CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)))
#the Cohen's d effect size for birth weight between first and other child is smaller than the pregnancy length effect size.
