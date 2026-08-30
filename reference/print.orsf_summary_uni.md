# Print ORSF summary

Print ORSF summary

## Usage

``` r
# S3 method for class 'orsf_summary_uni'
print(x, n_variables = NULL, ...)
```

## Arguments

- x:

  an object of class 'orsf_summary'

- n_variables:

  The number of variables to print

- ...:

  Further arguments passed to or from other methods (not currently
  used).

## Value

invisibly, `x`

## Examples

``` r

object <- orsf(pbc_orsf, Surv(time, status) ~ . - id, n_tree = 25)

smry <- orsf_summarize_uni(object, n_variables = 2)

print(smry)
#> 
#> -- ascites (VI Rank: 1) -------------------------
#> 
#>         |---------------- Risk ----------------|
#>   Value      Mean    Median     25th %    75th %
#>  <char>     <num>     <num>      <num>     <num>
#>       0 0.3087374 0.1859818 0.04183841 0.5614236
#>       1 0.4965395 0.4214549 0.30005793 0.7145065
#> 
#> -- bili (VI Rank: 2) ----------------------------
#> 
#>         |---------------- Risk ----------------|
#>   Value      Mean    Median     25th %    75th %
#>  <char>     <num>     <num>      <num>     <num>
#>    0.60 0.2404645 0.1342975 0.03456875 0.3904944
#>    0.80 0.2425520 0.1435297 0.03507037 0.3904944
#>    1.40 0.2625349 0.1554767 0.04820122 0.4168304
#>    3.52 0.3795922 0.3167143 0.15794919 0.5811623
#>    7.25 0.4682454 0.4348054 0.25161269 0.6726243
#> 
#>  Predicted risk at time t = 1788 for top 2 predictors 
```
