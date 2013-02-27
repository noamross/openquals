% Quals Reading: Model Comparison
% Noam Ross
% 12-12-23 08:39:51

[Andrew Latimer](http://www.plantsciences.ucdavis.edu/faculty/latimer/index.htm)
is having me read up on model comparison approaches for my qualifying exam. The
overarching question: "How do we compare and/or average models to select the
best one for purposes of prediction and illuminating mechanisms?"

@Friedman2001 (Chapter 7) - Model Assessment and Selection
==========================================================

Summary
-------

-   We use prediction error as a measure to assess and select models
-   Prediction error can be broken up into
    -   irreducible: stochasticity in the process
    -   model bias: difference between the best-fit model and the true process
    -   estimation bias: difference between the best-fit model and the actual
        fitted model
    -   variance: stochasticity in model fitting due to sampling

-   In general, there is a trade-off between bias and variance, with more
    complex models having less bias and higher variance. Model selection
    attempts to minimize prediction error by balancing the two.
-   Ideally, we would fit models to training data, validate to validation data
    to choose amongst them, and assess on test data to estimate the error of the
    final model
-   The difference between the error on the training data set and the prediction
    error is model **optimism**
-   AIC and $C_p$ assess prediction error by adding an optimism term to the
    error on training data
-   BIC is a similar measure, but is derived from an estimate of the posterior
    probability of models. It can also be derived from the minimum description
    length of the model. It favors parsimony over prediction more than AIC.
-   Structural risk minimization (SRM) includes the structural complexity of
    functions in addition to the number of parameters
-   Cross validation measures the total prediction error by repeatedly fitting
    the model to different sub-sets of the data
-   K-fold cross-validation splits the data into chunks and excludes a
    validation set each time. When K=1, you have leave-one out cross validation.
    This gives you relatively high variance but low bias.
-   Cross validation should be performed on the entire model selection
    procedure, not the final model or set of models, to get true prediction
    error
-   Bootstrapping fits the model on data sets generated from random sampling
    (with replacement) of the original.
-   Leave-one-out bootstrapping leaves out the original value on which error is
    estimated from the random sample
-   Bootstrapping is pessimistic at low sample size (estimates high variance),
    so the 0.632 and 0.632+ approximations correct for this
-   These methods all do better at estimating \**general* test error (from all
    potential training sets) than *training* test error (for the model on the
    particular training data)

Bias, Variance, Complexity
--------------------------

**Test error** is the error in prediction given a particular training set
$(\text{Err}_\tau)$. **Training error** is the error on the training set. Note
that training error decreases with model complexity, but test error may
increase. Error may take the form of teh squared or absolute errors, or the
likelihood.

We have two goals in looking at these values, model *selection* and *assessment*
(estimating the test error).

Ideally, we would split the data set into *three* parts: training (50%,
fitting), validation (25%, assessment for selection), and test (25%, estimating
final error). This requires a lot of data.

Error of a fit can be reduced:

$$\text{Err} = \text{Irreducible Error (Stochasticity)} + \text{Bias}^2 + \text{Variance} $$

The more complex the model, the lower the bias but the higher the variance. This
expression is tractable for some models, such as the linear model, where the
average error is:

$$ \frac{1}{N} \sum_{i=1}^N \text{Err}(x_i) = \sigma_\varepsilon^2 +  \frac{1}{N} \sum_{i=1}^N [f(x_i) - E\hat{f}(x_i)]^2 + \frac{p}{N} \sigma_\varepsilon^2 $$

Note that $p$ is the number of parameters.

Bias can be further broken down into **model bias** - the error between the
best-fitting model and the true function, and **estimation bias**, the error
between the average estimate and the best possible fit.

Note that bias-variance tradeoffs are different for classification errors (0-1
loss) than squared error losses.

Optimism of training error rate
-------------------------------

Training error is typically less than the true error. This difference is
*optimism*:

$$ \text{op} \equiv \text{Err_{in}} - \bar{\text{err}} $$

And the average optimism across all training sets is $\omega$. For many measures
of error, this is proportional to the covariance between the sample observations
and predictions:

\$\$ \omega = \frac{2}{N} \sum*{i=1}\^N \cov(\hat{y}\*i, y\_i)

The general error is the training error plus optimism. Some methods (e.g., AIC)
to estimate general error are to estimate optimism and add it to training error.
Others (cross validation), are direct estimates of the out-of-sample error.

Estimates of In-Sample Prediction Error
---------------------------------------

These take the form of $\hat{\bar{text{err}}} + \hat{\omega}$.

For squared-error loss, the $C_p$ statistic estimates in-sample prediction
error:

$$ C_p = \bar{\text{err}} + 2 \frac{d}{N}  \sigma_\varepsilon^2 $$

Where $d$ is the number of parameters.

For log-likelihood loss, we have the **Aikaike information criterion**

\$\$ \text{AIC} = -\frac{2}{N} \text{loglik} + 2 \frac{d}{N}

These are equivalent for a Gaussian model.

Effective number of parameters
------------------------------

The **effective number of parameters** is defined (for a linear model
$\boldsymbol S$) as

$$ \text{df}(\boldsymbol S) = \text{trace}(\boldsymbol S) $$

This replaces $d$ in the $C_p$ statistic

Bayesian Information Criterion
------------------------------

BIC is defined as:

$$\text{BIC} = -2 \text{loglik} + \log(N) d $$

This is proportional to AIC with the 2 factor replaced by $\log N$. BIC tends to
penalize complex models more heavily.

BIC arises not from a mimimization of prediction error, but a Bayesian estimate
of which model is most likely.

Note that we can also estimate the posterior probability of each model
$\mathscr{M}_m$ as

$$ \frac{e^{-\frac{1}{2} \text{BIC}_m} }{\sum^M e^{-\frac{1}{2} \text{BIC}_m}}  $$

BIC also arises from an approach of **minimum description lenghth**.

Vapnik-Chervonenkis Dimension
-----------------------------

VC theory gives a general measure of complexity $d$. Functions have different
complexities even with the same number of parameters. For instance, $\sin x$ is
more complex than $x$.

For indicator functions[^1], the VC dimension of a function is the largest
number of points that the function can can shatter (separate into distinct
classes) on a plane.

For linear functions, this value is 3, while $\sin (\alpha x)$ has infinite
dimension.

This can be generatlized to non-indicator functions. For such functions, the VC
dimension is that of the indicator class
$\left{ I(g(x,\alpha) - \beta > 0)\right} $, where $g$ is the general function
and $\beta$ is the range of values it takes.

Optimism increases with VC. The **structural risk minimiation** approach fits
nested models with different $h$ values and chooses

Cross-Validation
----------------

Cross validation estimates the expected extra-sample error, but typically can
not estimate the conditional error (for a given training set)

**K-fold Cross-Validation** splits the data into 5 or 10 parts, performing
validation on one part while training on the rest, repeating across all
combinations. The error for each permutations are averaged.

For $K=N$, this is called **leave-one-out** cross validation. This
computationally expensive, but also has very similar "training sets", meaning
results have high variance for out-of-sample predictions.

A typical rule for cross-validation is to choose the simplest model whose error
is no more than one standard error above the best model.

**Generalized cross-validation** is an analytic approximation to leave-one-out
cross-validation for linear models:

$$ \text{GCV}(\hat{f}) = \frac{1}{N} \sum_1^n \left[\frac{y_i - \hat{f}(x_i)}{1 - \text{trace}(\boldsymbol S) / N}\right]  $$

$\boldsymbol S$ is the effective number of parameters.

Note that cross-validation should not be used to predict error on a subset of
already-fit models, but to predict error using ALL models - e.g., first split
the data, then fit and select models, then do so again. Do not split data after
fitting models.

Bootstrap Methods
-----------------

In the bootstrap, we randomly draw with replacement from the dataset, generating
random datasets the same size as the original. Then we refit to each of these,
and test against the original dataset.

If we estimate prediction error via the variance in bootstrap fits, it will be
optimistic because of overlap in training sets.

Leave-one-out bootstrap uses the variance in predictions of each sample, using
only bootstraps excluding that sample. This will roughly behave like twofold
cross-validation, because the average number of distinct observations in each
bootstrap is $0.632 N$. If the data set is small, the error will be biased
upwards. This can be corrected with the 0.632 estiamte and the **relative
overfitting rate** (see p. 270) of the reading.

Comparison
----------

AIC and BIC, cross-validation and bootstrap perform similarly in model
selection, but the latter two provide better estimates of test error.

Conditional test error is hard to predict in general, but expected test error is
much more reasonable.

@Gelfand1998 - Model choice: a minimum posterior predictive loss approach
=========================================================================

Introduction
------------

-   Heirarchical models, with random terms, have uncertain dimension that
    changes with sample sizes, but classic model-comparison measures do not
    consider this.
-   Bayesian approaches use $p(y_{\text{obs}} \vert m)$ as a screning criterion.
    Ratios of this between models are *Bayes factors*
-   When non-flat prior are used for complex hierarchical models, Bayes factors
    are difficult to intepret
-   The approach here minimizes the expected loss of out-of-sample prediction,
    conditional on the obervations (conditional test areas)
-   This value can be interpreted as penalized deviance (kind of like AIC) but
    does not require model dimension

Utility ideas
-------------

The goal is to calculate the minimum (across models) expected minimized loss
function for out-of-sample data

The loss function is

$$L(y_{l,\text{out}}, a_l; y_{\text{in}} = L(y_{l,\text{out}}, a_l) + kL(y_{l,\text{in}}, a_l)$$

That is, the out-of-sample loss is the sum the loss of fitting the model to
out-of-sample data plus *k* times the loss of the in-sample data.

For a gaussian model, this term is:

Variance of the out-of-sample prediction + (Best guess - mean of out-of-sample
prediction)\^2 + k(Best guess - Observation)\^2

In the gaussian case, with the best guess minimized, and $k \rightarrow \infty$,
we get

$$L(m) \equiv D(m) = \sum_i^n (\mu_i^m - y_{i,\text{in}})^2 + \sum_i^n \sigma_i^{2,m} $$

This is simply the loss function for the model on the training data plus the
variance of the predicted values. With flat priors in a linear model the latter
term is approximately $$\sigma^2 (n + p) $$.

An approximation the general case of loss functions and non-gaussian models is:

$$D(m) \approx \sum_i^n L(\mu_i^m, y_{i,\text{out}}) + b_i^m \sigma_i^{2,m}$$

Where
$$b_i^m = \frac{1}{2} \frac{\partial^2 L(\mu_l^m, y_{i,\txt{out}})}{\partial y^2}$$

Again, this is a combination of a goodness-of-fit penalty and a penalty function
on model variance

Deviance loss functions
-----------------------

@Spiegelhalter2002 - Bayesian measures of model complexity and fit
==================================================================

In complex heirarchical models, parameters may outnumber observations and
traditional BIC may not apply.

$p_D$ is the effective number of parameters, defined as the difference between
the posterior mean deviance and the deviance at posterior estimates of
parameters of interests. It can be solved for numerically with MCMC

Together with $\bar{D}$, the posterior mean deviance, $p_D$ provides the
*deviance information criterion*.

Complexity in Bayesian models
=============================

In a hierarchical model, depending on the parameters of interest (or *focus*),
complexity may vary within identical model structures. Also, priors reduce
effective parameter numbers.

To test, we posit future unoberved data $Y$, which the model $\theta$ would
predict correctly. As observed data $y$ increases, $p(Y \vert \theta^t)$
approaches $p^t(Y)$

Residual information in the data, conditional on the model $\theta$, is
$-2 \log p(y | \theta)$. The difference between this and and residual
information in the "true" model $\theta^t$ is the deviance, or $d_\Theta$.
Measures of model dimensionality differ in how to deal with with the unknown
"true" parameters.

In a likelihood context, the expected deviance the true model is estimated from
the maximum likelihood model. It is $p^* = \text{tr}(KJ^{-1})$, where

$$ J = -E^t \left[ \frac{\partial^2 \log p(Y|\theta^t) }{\partial \theta^2} \right] $$

\$\$ K = \text{var}\^t \left[
\frac{\partial \log p(Y|\theta^t) }{\partial \theta}

Or, $p^* = \tr{J\Sigma}$, when $\Sigma$ is an approximation of the
variance-covariatnce matrix of the model $(J^{-1} K J^{-1})$

From a Bayesian perspective, we replace the unknown $\theta^t$ with unknown
random variable $\theta$.

$$\begin{aligned}
  p_D(y, \Theta, \tilde{\theta}(y)) &= E_{\theta | y} (d_\Theta (y,\theta,\tilde\theta (y)))\\
  &= E[-2 \log (p(y_\theta))] + 2 log(p(y|\tilde\theta (y))$$

$p_D$ is a proposal for the effectiv number of parameters. In essence, it is the
expected (mean) deviance of a random parameteriation of the model from the
maximum likelihood model.

When our maximum-likelihood estimate is the mean of the posterior (gaussian
case), and focus is not important, then

$$p_D = \overline{D(\theta)} - D(\bar{theta})$$

Where $D$ is the "Bayesian deviance":

$$D(\theta) = -2 \log (p(y| \theta)) + 2 \log (f(y))$$

That is $p_D$ is the "mean deviance minus the deviance of the means." $f(y)$ is
a standardizing function on the data, for instance, the probability of a model
that exactly reproduces the data.

Note that $\overline{D(\theta)}$ takes the form of deviance plus $p_D$, the
measure of model complexity.

By applying Bayes' theorem to $p_D$, we find that it is $(-2\times)$ the
posterior estimate of how much the data improves our knowledge of the model in
general, minus how much it improves a particular (maximum likelihood estimate)
of the model.

Note that this measure depends on using the posterior mean, rather than mode or
median, as our model estimate. This means the meaure depends on how we estimate
the model.

$p_D$ should be positive for any unimodal (concave) posterior.

Note that $p_D$ onlu works conditional on the idea that there is a "true" model.

$p_D$ is easily calculated using MCMC output.

Approximations of $p_D$
-----------------------

For a normal likelihood distribution, $p_D$ can be approximated as

$$D(\bar{\theta}) + \tr(-L_{\bar\theta}^{''} V)$$

Where $L_{\bar\theta}$ is the likelihood of the mean model and $V$ is the
covariance matrix of $\theta$. This can be thought of how much the information
in the likelihood is about the parameters, rather than model structure or prior.
It is exact for normal, linear models. $p_D$ is also equal to the trace of the
"hat" matrix, which projects the data onto fitted values.

If the prior is flat or negligible, then $p_D$ is approximately $p$, the number
of parameters.

$p_D$ in simulation
-------------------

For a hierarchical model, of several groups, for a binomial likelihood with a
conjugate prior:

-   As group sample size increases, the group's contribution to the effective
    number of parameters approaches 1
-   When the prior is very strong and conflicts with the data, $p_D$ is differnt
    across median, mean, and peak likelihood choices

These observations hold across other exponential models.

Model selection
---------------

$\bar{D(\theta)}$ is a measure of model fit or adequacy

Classic model selection minimizes model loss + optimism.

For expoential families across different loss functions, optimism $(\pi)$ is:

$$\pi(\theta^t) = 2 \sum_i \cov^t (\hat{Y}_i, Y_i)$$. For linear models, this
equals $2p$.

The authors propose DIC, or the **deviance information criterion** as

$$\text{DIC} = D(\bar\theta) + 2p_D = \bar{D(\theta)} + p_D$$

DIC is likely to also be strongly corelated to cross-validation, like AIC. Like
BIC, it requires the assumption of a true model, though not in the actual model
set. It is unkown whether it can be used for model averaging.

Recommend using several different measures (mean, median, mode) with non-normal
models

Nuisance parameters should be integrated out prior to estimation.

Examine the error in $\bar{D}$ to determine how significant the differences
between DIC values are.

Discussion
==========

$p_D$ is best for understanding the variation in complexity due to priors. Note
even flat priors reduce it below the number of parameters.

> Given the number of approximations and assumptions that are required to obtain
> the DIC it can only really be used as a broad brush technique for
> discriminating between obviously disparate models, inmuch the same way as any
> of the alternative information criteria suggested above might be used.

@Cressie2009 - Accounting for uncertainty
=========================================

Hierearchical modeling builds data, process, and (optional) parameter models.

Modeling in the presence of uncertainty
---------------------------------------

Curve-fitting with additive error doesn't separate out different sources of
uncertainty (e.g. process and measurement)

Statistical modeling determines the parameters of a *distribution* that maximize
likelihood. This is a data model, and uncertainty is due to sampling and
measurement.

In stochastic modeling, the uncertainty is in the process.

A hierarchical model models noth with two conditional distributions: The data,
conditional on the ecological process and the parameters of the observation
process, and the ecological process, conditional on ecoogical parameters, as
such:

$$[D,E | P_D, P_E] = [D | E, P_D][E | P_E]$$

Such as model can represent the joint probabilities of multiple variables as:

$$ [A,B,C] = [A|B,C][B|C][C]$$

An analogous model that incorporates parameter uncertainty is

$$[D,E,P][D|E,P][E|P][P] = [D,E, P_D][E|P_E][P_D, P_E]$$

In statistical inference, $\hat{P}$ is substituted for $P$. Variability in $P$
can be difficult to assess.

Inference is often not just to understand the variability $[E|D]$, but also $E$
across other potential samples of $D$.

This appproach is useful with multiple, different data sets, which can be
modeled as independent but conditional on the same ecological process and a
joint parameter set $P_D$. It can also model multiple ecological processes.

When multiple ecological processes are in the model, we can add a level of
heirarchy where they are dependent on a higher-level process.

It is often possible to simplify the joint conditional probabilities, as in the
assumption that a time series is a Markov process.

Design for data collection
--------------------------

Sampling should start with specification of the population under study.

Main principles of design are stratification, randomization, and replication.
Stratification allows modeling of variation. Randomization avoids bias in
sampling choice. Replication decreases variabiity within strata.

Statistical design helps optimize the balance between statification and
replication. Design-based inference can be robust, while model-based inference
can be efficient. Model-based design can be made more efficient by using the
process model to change sampling regimes over time.

For design-based inference, the source of variability is the externally imposed
probability of sampling. Many design regimes are designed to be ignorable. That
is, the sampling probability is independent of the ecological process. In this
case, you have purely model-based inference. In purely observational studies
without randomization, there is no imposed probability of sampling, BUT there is
no ability to make inference beyond the sample.

Statistical Inference in Ecological Analyses
--------------------------------------------

[^1]: Functions for classification
