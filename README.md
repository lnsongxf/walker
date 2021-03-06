[![Build Status](https://travis-ci.org/helske/walker.png?branch=master)](https://travis-ci.org/helske/walker)
[![cran version](https://www.r-pkg.org/badges/version/walker)](https://cran.r-project.org/package=walker)
[![downloads](https://cranlogs.r-pkg.org/badges/walker)](https://cranlogs.r-pkg.org/badges/walker)
[![codecov](https://codecov.io/gh/helske/walker/branch/master/graph/badge.svg)](https://codecov.io/gh/helske/walker)

# walker: Efficient Baysian dynamic linear regression models with Stan/R

Walker provides a method for fully Bayesian generalized linear regression where the 
regression coefficients are allowed to vary over "time" as a first or second order integrated random walk. 

The Markov chain Monte Carlo (MCMC) algorithm uses Hamiltonian Monte Carlo provided by Stan, 
using a state space representation of the model in order to marginalise over the coefficients for accurate and efficient sampling.
For non-Gaussian models the MCMC targets approximate marginal posterior based on Gaussian approximation, which is then corrected using 
sequential Monte Carlo as in [Vihola, Helske, Franks (2018)](https://arxiv.org/abs/1609.02541).

See the package [vignette](http://htmlpreview.github.io/?https://github.com/helske/walker/blob/master/walker_html/walker.html) for details and an examples.


# NEWS

### 20.9.2019

* Switched from GPL2+ to GPL3 in order to be compatible with future Stan versions.

### 04.03.2019

* Added methods fitted and coef for extracting the posterior means and and regression coefficents from the 
  walker_fit object.
* Fixed issue with Makevars and clang4 per request by CRAN.
* Added option to predict on mean-scale, e.g, probabilities instead of 0/1 in Bernoulli case.
* Fixed a bug in the Gaussian predictions, last time point was missing the observational level noise.

### 25.02.2019

* Issue with upcoming staged installation in CRAN fixed by Tomas Kalibera.

### 14.02.2019

* Dimension bug in GLM case fixed.

### 8.11.2018

* Fixed StanHeaders search in Makevars. 

### 22.10.2018

* Pull request by Ben Goodrich for fixing the issue with clang4. New version on it's way to CRAN.

### 15.10.2018
* Missing values in response variable are now supported.
* Added gamma variables to models which can be used to damp the variance of the random walks. 
* Tidied some Stan codes in order to reduce deep copying.
* Moved stan codes under `src`.
* Increased the iteration counts in examples in order to pass CRAN tests.
<