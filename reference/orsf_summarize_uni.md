# Univariate summary

Summarize the univariate information from an ORSF object

## Usage

``` r
orsf_summarize_uni(
  object,
  n_variables = NULL,
  pred_horizon = NULL,
  pred_type = NULL,
  importance = NULL,
  class = NULL,
  verbose_progress = FALSE,
  ...
)
```

## Arguments

- object:

  (*ObliqueForest*) a trained oblique random forest object (see
  [orsf](https://docs.ropensci.org/aorsf/reference/orsf.md)).

- n_variables:

  (*integer*) how many variables should be summarized? Setting this
  input to a lower number will reduce computation time.

- pred_horizon:

  (*double*) Only relevent for survival forests. A value or vector
  indicating the time(s) that predictions will be calibrated to. E.g.,
  if you were predicting risk of incident heart failure within the next
  10 years, then `pred_horizon = 10`. `pred_horizon` can be `NULL` if
  `pred_type` is `'mort'`, since mortality predictions are aggregated
  over all event times

- pred_type:

  (*character*) the type of predictions to compute. Valid Valid options
  for survival are:

  - 'risk' : probability of having an event at or before `pred_horizon`.

  - 'surv' : 1 - risk.

  - 'chf': cumulative hazard function

  - 'mort': mortality prediction

  - 'time': survival time prediction

  For classification:

  - 'prob': probability for each class

  For regression:

  - 'mean': predicted mean, i.e., the expected value

- importance:

  (*character*) Indicate method for variable importance:

  - 'none': no variable importance is computed.

  - 'anova': compute analysis of variance (ANOVA) importance

  - 'negate': compute negation importance

  - 'permute': compute permutation importance

- class:

  (*character*) only relevant for classification forests. If `NULL` (the
  default), summary statistics are returned for all classes in the
  outcome, and printed summaries will show the last class in the class
  levels. To specify a single class to summarize, indicate the name of
  the class with `class`. E.g., if the categorical outcome has class
  levels A, B, and C, then using `class = "A"` will restrict output to
  class A.

  For details on these methods, see
  [orsf_vi](https://docs.ropensci.org/aorsf/reference/orsf_vi.md).

- verbose_progress:

  (*logical*) if `TRUE`, progress will be printed to console. If `FALSE`
  (the default), nothing will be printed.

- ...:

  Further arguments passed to or from other methods (not currently
  used).

## Value

an object of class 'orsf_summary', which includes data on

- importance of individual predictors.

- expected values of predictions at specific values of predictors.

## Details

If `pred_horizon` is left unspecified, the median value of the
time-to-event variable in `object`'s training data will be used. It is
recommended to always specify your own prediction horizon, as the median
time may not be an especially meaningful horizon to compute predicted
risk values at.

If `object` already has variable importance values, you can safely
bypass the computation of variable importance in this function by
setting importance = 'none'.

## See also

as.data.table.orsf_summary_uni

## Examples

``` r

object <- orsf(pbc_orsf, Surv(time, status) ~ . - id, n_tree = 25)

# since anova importance was used to make object, it is also
# used for ranking variables in the summary, unless we specify
# a different type of importance

orsf_summarize_uni(object, n_variables = 2)
#> 
#> -- ascites (VI Rank: 1) -------------------------
#> 
#>         |---------------- Risk ----------------|
#>   Value      Mean    Median     25th %    75th %
#>  <char>     <num>     <num>      <num>     <num>
#>       0 0.3015582 0.2260172 0.05061925 0.5094704
#>       1 0.4399066 0.3806282 0.21066049 0.6766038
#> 
#> -- bili (VI Rank: 2) ----------------------------
#> 
#>         |---------------- Risk ----------------|
#>   Value      Mean    Median     25th %    75th %
#>  <char>     <num>     <num>      <num>     <num>
#>    0.60 0.2513342 0.1518283 0.04385794 0.3892157
#>    0.80 0.2550326 0.1567469 0.04852839 0.3913328
#>    1.40 0.2728825 0.1957005 0.06644606 0.4149212
#>    3.52 0.3575481 0.3080642 0.13239033 0.5404010
#>    7.25 0.4546721 0.4081686 0.25099206 0.6485875
#> 
#>  Predicted risk at time t = 1788 for top 2 predictors 

# if we want to summarize object according to variables
# ranked by negation importance, we can compute negation
# importance within orsf_summarize_uni() as follows:

orsf_summarize_uni(object, n_variables = 2, importance = 'negate')
#> 
#> -- bili (VI Rank: 1) ----------------------------
#> 
#>         |---------------- Risk ----------------|
#>   Value      Mean    Median     25th %    75th %
#>  <char>     <num>     <num>      <num>     <num>
#>    0.60 0.2513342 0.1518283 0.04385794 0.3892157
#>    0.80 0.2550326 0.1567469 0.04852839 0.3913328
#>    1.40 0.2728825 0.1957005 0.06644606 0.4149212
#>    3.52 0.3575481 0.3080642 0.13239033 0.5404010
#>    7.25 0.4546721 0.4081686 0.25099206 0.6485875
#> 
#> -- copper (VI Rank: 2) --------------------------
#> 
#>         |---------------- Risk ----------------|
#>   Value      Mean    Median     25th %    75th %
#>  <char>     <num>     <num>      <num>     <num>
#>    25.5 0.2443431 0.1635872 0.04039580 0.3885730
#>    42.8 0.2532196 0.1577342 0.04094236 0.3816909
#>    74.0 0.2825893 0.1941957 0.05571884 0.4381673
#>     129 0.3404826 0.2643601 0.12559610 0.5036362
#>     214 0.4148122 0.3460876 0.21514558 0.6128151
#> 
#>  Predicted risk at time t = 1788 for top 2 predictors 

# for multi-category fits, you can specify which class
# you want to summarize:

object =  orsf(species ~ ., data = penguins_orsf, n_tree = 25)

orsf_summarize_uni(object, class = "Adelie", n_variables = 1)
#> 
#> -- bill_length_mm (VI Rank: 1) -------------------
#> 
#>         |------------- Probability -------------|
#>   Value      Mean     Median     25th %    75th %
#>  <char>     <num>      <num>      <num>     <num>
#>    36.6 0.6830776 0.84544074 0.32069482 0.9803987
#>    39.5 0.6482196 0.81423080 0.26784874 0.9706868
#>    44.5 0.3577357 0.30291802 0.01926994 0.6328028
#>    48.6 0.1951207 0.13157895 0.01474271 0.3016239
#>    50.8 0.1460624 0.08585581 0.01316055 0.2415948
#> 
#>  Predicted probability for top 1 predictors 

```
