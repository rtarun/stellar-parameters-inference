Paper:
https://arxiv.org/pdf/1411.1073.pdf

Big idea of and in the paper:
This machine learning framework will allow fundamental parameters to be determined without 
the need for additional spectroscopy.


Bigger Idea:
Build data driven methods to learn relationships between observables and parameters of interest 
without relying on parametric physical models.


Problem:
there are more than 10^9 photometrically cataloged sources, yet modern spectroscopic surveys are
limited to ~10^6 targets.


Solution:
a machine-learning framework capable of inferring fundamental stellar parameters (Teff, log g, and [Fe/H]) 
using photometric-brightness variations and color alone.

Why do it this way?
- To estimate stellar properties, photometric measurements cheaper than spectroscopic measurements

Parameters being inferred: 
Teff, log g, and [Fe/H]


Data description:
- variable stars
- Stripe 82 (equatorial region of southern Galactic cap)
- in each of ugriz filters
- 334 features: 66 each for ugriz filters, as well as the 4 SDSS colors
example: the amplitude of variations delta g, 
the best-fit period Pg, 
the standard deviation sigma g, 
the MAD of the Lomb-Scargle residuals divided by the MAD of the raw light
curves, 
scatter res raw, 
the Stetson variability index J, 
the lightcurve skewness g, 
and the quasar and non-quasar variability metrics, (chi sqr)QSO/v and (chi sqr)non-qso/v

why this?

Algorithm:
Randon Forest Regression (RFR)
- Aggregate results from several decision trees to provide low-bias low-variance estimate of the properties of interest
- each node of the tree new splitting parameter can only be selected from a random subset of mtry features in entire feature set.
- Each parameter estimate comes from a separate model.


Why RFR?

- Fast and easy to interpret
- good at handling tabular data with numerical features, or categorical features with fewer than hundreds of categories. 
- Unlike linear models, random forests are able to capture non-linear interaction between the features and the target.

Tuning parameters for RFR:
1. ntree: total number of decision trees used to construct the forest; here, 5 (rule of thumb)
2. mtry: number of features that are used as potential splitting criterion in each non-terminal node of the tree;
here, sqrt(n) where n is total numbrer of features used in model
3. nodesize: Minimum size of terminal nodes; setting this number larger causes smaller trees to be grown; here, nodesize = 5


Optimizing models:


Model biases:


Papers that reference this paper:
- A recurrent neural network for classification of unevenly sampled variable stars
https://www.nature.com/articles/s41550-017-0321-z#ref-CR11

Acronyms and definitions:
- DES: Dark Energy Survey
- Feature: Metric describing a source, can be real-numbered or categorical
- Hectospec: a multi-object spectrograph on the 6.5-m Multi-Mirror Telescope (MMT).
- HET: Hoberly-Eberly Telescope
- SEGUE: Sloan Extension for Galactic Understanding and Exploration
- SSPP: SEGUE Stellar Parameters Pipeline
- SNR: Signal to Noise ratio 
- Stripe 82: equatorial region of southern Galactic cap
- MMT: Multi-Mirror Telescope
- UWVSC: University of Washington Visual Survey Catalog




