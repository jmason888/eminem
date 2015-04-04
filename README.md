# M&amp;M statistical simulation

This R Markdown code explores the issues with a misspecified ANOVA model
for investigating the homogeneity of the distribution of colors within
packages of M&M candies.

The data-generating model is that boxes of M&Ms are assumed to be filled
with a _fixed_ number of candies, drawn at random from an infinite vat
containing unknown proportions of each color.
The research question is whether the colors in this vat are in
_equal proportions_, or whether those _proportions differ_.

To answer this question, a researcher proposes to draw a sample of
boxes of M&Ms, and count the numbers of each color in each box.
ANOVA would then be conducted to see if the counts
differ between the colors, using the color for group membership
and the count as the outcome variable. Thus, if there are
*c* different colors of M&M, and *N* boxes were sampled,
*cN* data points would be entered into ANOVA, *c* for each box.
This model is missepcified because the count of colors
are _not independent_ within each box: for example if the
box is mostly full of blue candies, there will be less
room for each of the other colors.

For the statistical test implied by
the ANOVA model, hypothesis test is as follows:

* H<sub>0</sub>: The colors in the vat are in equal proportion.
* H<sub>A</sub>: At least one color in the vat has a different
proportion than the others.

In a correctly-sepecified model,  if the null hypothesis is true,
with a significance threshold of *a*,
we would expect to obtain a p-value < *a*
(and thus falsely reject the null hypothesis)
in exactly *a* proportion of experiments. 
(For example if our siginificance threshold is p<0.05,
then we would expect to falsely reject the null 20% of
the time).  This is, in fact, the _definition_ of the
p-value, and thus
the _sampling distribution of p-values_ should have
a cumulative distribution function (CDF) which is:

* g(p) = 1 if 0 < p < 1
* g(p) = 0 otherwise

