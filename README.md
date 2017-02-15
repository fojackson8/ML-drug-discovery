# ML-drug-discovery

This is a template script written in R, for benchmarking different supervised machine learning algorithms on a
high-dimensional dataset. The specific filenames and variables I included in my research have been removed and 
replaced with generic names. This is because the paper is not yet published. 

Specifically, this script will first make the necessary adjustments on the dataset to make it ready for classification.
Then Random Forests (ref 1) and Gradient boosting (ref 2) are both run on the data, with parameters tuned to my results. 
This tuning is an empirical process, and although it's slightly more complicated for GB than RF, clear documentation
for all tuning parameters can be found in the two references provided.

This script first randomly partitions the data into training and test sets. It then runs the analysis and returns confusion 
tables for each analysis, which give the number of true positives, false positives and false negatives. Kappa is also calculated. 

The Random Forests package is first used to generate variable importance and partial dependency plots. Variable importance 
plots show the relative importance of each variable in predicting the outcome (%increase in predictive error if variable was 
removed). The partial dependency plots show how the values of each variable affect the response variable.

The GBM package does not contain similar variable-specific metrics. This script does however contain a line that facilitates 
benchmarking of the gradient boosting method: the command 'best.iter' allows you to visualise how predictive error decreases
with number of iterations.

Finally, to compare classical regression against machine learning methods, this script contains a template for running a 
generalised additive model of regression on an example dataset. Suitable tuning parameters are selected, and smoothers are 
placed on all numerical variables. Again, a confusion table is generated to allow comparison of false positives and negatives.

I found for my analysis that Random Forests achieved the most stable and accurate prediction of my outcome variable. However 
this will vary, and will likely depend on factors such as depth vs. breadth of dataset. The confusion tables generated provide a simple and clear way to compare the perfomance of each classification algorithm, whilst the kappa statistic takes into account any sampling biases in your data.
