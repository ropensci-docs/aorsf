# Automatic variable values for dependence

For partial dependence and individual conditional expectations, this
function allows a variable to be considered without having to specify
what values to set the variable at. The values used are based on
quantiles for continuous variables (10th, 25th, 50th, 75th, and 90th)
and unique categories for categorical variables.

## Usage

``` r
pred_spec_auto(...)
```

## Arguments

- ...:

  names of the variables to use. These can be in quotes or not in quotes
  (see examples).

## Value

a character vector with the names

## Details

This function should only be used in the context of `orsf_pd` or
`orsf_ice` functions.

## Examples

``` r

fit <- orsf(penguins_orsf, species ~., n_tree = 5)

orsf_pd_oob(fit, pred_spec_auto(flipper_length_mm))
#> Key: <class>
#>         class flipper_length_mm      mean         lwr       medn   upr
#>        <fctr>             <num>     <num>       <num>      <num> <num>
#>  1:    Adelie               185 0.6510597 0.008691406 0.93333333     1
#>  2:    Adelie               190 0.6376856 0.007812500 0.93333333     1
#>  3:    Adelie               197 0.6051195 0.007812500 0.93170380     1
#>  4:    Adelie               213 0.4517576 0.007812500 0.48514851     1
#>  5:    Adelie               221 0.4441207 0.007812500 0.48514851     1
#>  6: Chinstrap               185 0.3277862 0.009615385 0.06848291     1
#>  7: Chinstrap               190 0.3462555 0.009615385 0.08347478     1
#>  8: Chinstrap               197 0.3591037 0.009615385 0.08670635     1
#>  9: Chinstrap               213 0.4371854 0.009900990 0.33333333     1
#> 10: Chinstrap               221 0.4010776 0.009900990 0.33333333     1
#> 11:    Gentoo               185 0.5947110 0.057954545 0.50000000     1
#> 12:    Gentoo               190 0.6487316 0.062500000 0.65885417     1
#> 13:    Gentoo               197 0.8075340 0.071428571 0.99218750     1
#> 14:    Gentoo               213 0.6520185 0.047619048 0.95000000     1
#> 15:    Gentoo               221 0.6525966 0.047619048 0.93828125     1
```
