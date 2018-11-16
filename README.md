# The Database of Dietary Supplement Adverse Events (DDSAE)

The Database of Dietary Supplement Adverse Events (DDSAE) is a collection of dietary supplement - adverse event signals
detected from the CFSAN Adverse Event Reporting System (CAERS). It contains adverse event signals detected for
both dietary supplement products and ingredients. We used four signal detection methods:

1. Proportional Reporting Ratio (**PRR**)
2. Reporting Odds Ratio (**ROR**)
3. Bayesian Confidence Propogation Neural Network (**BCPNN**), in which the information component (IC) metric was estimated using 50,000 Monte Carlo simulations.
4. Gamma Poisson Shrinker (**GPS**) 


## Directory structure
The detected adverse events are within two subdirectories of `data/`:

* `ingredient_adverse_events/`: Detected dietary supplement ingredient - adverse event associations.
* `product_adverse_events/`: Detected dietary supplement product - adverse event associations.

Each of these subdirectories contains four CSV files containing the ranked pairs detected by each of the four methods. 


## File structure
All files contain the following columns:

* `{ingredient,product}`: The ingredient (under `ingredient_adverse_events`) or product (for `product_adverse_events`) in each detected association.
* `adverse_event`: The adverse event in each detected association. These are coded according to the Medical Data Dictionary for Regulatory Activities (MedDRA).
* `count`: The number of times this pair occurred in CAERS.

In addition to these three columns, each CSV file contains a fourth column corresponding to the detection metric associated with that signal detection method.
The detection metrics are:

* PRR: **PRR05**, the lower bound of the 95% confidence interval. A signal was detected if the PRR05 >= 1.
* ROR: **ROR05**, the lower bound of the 95% confidence interval. A signal was detected if the ROR05 >= 1.
* BCPNN: **IC025**, the 2.5% quantile of the posterior distribution of IC. A signal was detected if the IC025 > 0.
* GPS: **EB05**, the lower bound of the 95% CI. A signal was detected if the EB05 >= 2.


## Using the dataset
Use of this dataset is subject of the terms of the LICENSE.

If you use our dataset in your work, please cite the corresponding paper:

*Vasilakes J, Rizvi R, Zhang J, Adam T, Zhang R. "Detecting Signals of Dietary Supplement Adverse Events from the CFSAN Adverse Event Reporting System (CAERS)". 
AMIA Jt Summits Transl Sci Proc. Forthcoming.*
