# Package index

## Oblique random forests (RFs)

Fit, inspect, summarize, and apply oblique RFs

- [`orsf()`](https://docs.ropensci.org/aorsf/reference/orsf.md)
  [`orsf_train()`](https://docs.ropensci.org/aorsf/reference/orsf.md) :
  Oblique Random Forests
- [`orsf_update()`](https://docs.ropensci.org/aorsf/reference/orsf_update.md)
  : Update Forest Parameters
- [`print(`*`<ObliqueForest>`*`)`](https://docs.ropensci.org/aorsf/reference/print.ObliqueForest.md)
  : Inspect Forest Parameters
- [`predict(`*`<ObliqueForest>`*`)`](https://docs.ropensci.org/aorsf/reference/predict.ObliqueForest.md)
  : Prediction for ObliqueForest Objects
- [`orsf_summarize_uni()`](https://docs.ropensci.org/aorsf/reference/orsf_summarize_uni.md)
  : Univariate summary
- [`print(`*`<orsf_summary_uni>`*`)`](https://docs.ropensci.org/aorsf/reference/print.orsf_summary_uni.md)
  : Print ORSF summary

## Control how your oblique RF works

Choose how to identify linear combinations of predictors and set tuning
parameters for your approach

- [`orsf_control()`](https://docs.ropensci.org/aorsf/reference/orsf_control.md)
  [`orsf_control_classification()`](https://docs.ropensci.org/aorsf/reference/orsf_control.md)
  [`orsf_control_regression()`](https://docs.ropensci.org/aorsf/reference/orsf_control.md)
  [`orsf_control_survival()`](https://docs.ropensci.org/aorsf/reference/orsf_control.md)
  : Oblique random forest control
- [`orsf_control_cph()`](https://docs.ropensci.org/aorsf/reference/orsf_control_cph.md)
  : Cox regression ORSF control
- [`orsf_control_custom()`](https://docs.ropensci.org/aorsf/reference/orsf_control_custom.md)
  **\[superseded\]** : Custom ORSF control
- [`orsf_control_fast()`](https://docs.ropensci.org/aorsf/reference/orsf_control_fast.md)
  : Accelerated ORSF control
- [`orsf_control_net()`](https://docs.ropensci.org/aorsf/reference/orsf_control_net.md)
  : Penalized Cox regression ORSF control

## Variable importance/selection

Estimate the importance of individual variables and conduct variable
selection using ORSFs

- [`orsf_vi()`](https://docs.ropensci.org/aorsf/reference/orsf_vi.md)
  [`orsf_vi_negate()`](https://docs.ropensci.org/aorsf/reference/orsf_vi.md)
  [`orsf_vi_permute()`](https://docs.ropensci.org/aorsf/reference/orsf_vi.md)
  [`orsf_vi_anova()`](https://docs.ropensci.org/aorsf/reference/orsf_vi.md)
  : Variable Importance
- [`orsf_vint()`](https://docs.ropensci.org/aorsf/reference/orsf_vint.md)
  : Variable Interactions
- [`orsf_vs()`](https://docs.ropensci.org/aorsf/reference/orsf_vs.md) :
  Variable selection

## Partial dependence and individual conditional expectations

Interpret your model by generating partial dependence or individual
conditional expectation values. Plotting functions not included (but see
examples)

- [`orsf_ice_oob()`](https://docs.ropensci.org/aorsf/reference/orsf_ice_oob.md)
  [`orsf_ice_inb()`](https://docs.ropensci.org/aorsf/reference/orsf_ice_oob.md)
  [`orsf_ice_new()`](https://docs.ropensci.org/aorsf/reference/orsf_ice_oob.md)
  : Individual Conditional Expectations
- [`orsf_pd_oob()`](https://docs.ropensci.org/aorsf/reference/orsf_pd_oob.md)
  [`orsf_pd_inb()`](https://docs.ropensci.org/aorsf/reference/orsf_pd_oob.md)
  [`orsf_pd_new()`](https://docs.ropensci.org/aorsf/reference/orsf_pd_oob.md)
  : Partial dependence
- [`pred_spec_auto()`](https://docs.ropensci.org/aorsf/reference/pred_spec_auto.md)
  : Automatic variable values for dependence

## Example survival data

Datasets used in examples and vignettes.

- [`pbc_orsf`](https://docs.ropensci.org/aorsf/reference/pbc_orsf.md) :
  Mayo Clinic Primary Biliary Cholangitis Data
- [`penguins_orsf`](https://docs.ropensci.org/aorsf/reference/penguins_orsf.md)
  : Size measurements for adult foraging penguins near Palmer Station,
  Antarctica

## Miscellaneous

Functions that don’t fit neatly into a category above, but are still
helpful.

- [`as.data.table(`*`<orsf_summary_uni>`*`)`](https://docs.ropensci.org/aorsf/reference/as.data.table.orsf_summary_uni.md)
  : Coerce to data.table
- [`orsf_time_to_train()`](https://docs.ropensci.org/aorsf/reference/orsf_time_to_train.md)
  : Estimate training time

## Back-end functions

Techniques used by aorsf that may be helpful in other contexts.

- [`orsf_scale_cph()`](https://docs.ropensci.org/aorsf/reference/orsf_scale_cph.md)
  [`orsf_unscale_cph()`](https://docs.ropensci.org/aorsf/reference/orsf_scale_cph.md)
  : Scale input data
