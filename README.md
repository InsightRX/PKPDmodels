# PKPDmodels

This repository contains definitions of PK/PD models used in the InsightRX
platform.

These models can be installed as R packages using the
[PKPDsim](https://CRAN.R-project.org/package=PKPDsim) package:

```r
library("PKPDsim")
model_from_api("models/pk_vanco_anderson.json5", to_package = TRUE, install_all = TRUE)
```

Please note that these models may differ from those used in production by
InsightRX. They are provided for demonstration purposes only, and should not be
used for dosing patients.

## Example usage

To simulate PK, provide the model and parameters to `PKPDsim::sim()` along with
a dosing regimen and covariates.

```r
library("PKPDsim")

## Create dosing regimen and covariates
reg <- new_regimen(
  amt = 100,
  n = 3,
  interval = 12,
  type = "infusion",
  t_inf = 1
)

covs <- list(
  WT = new_covariate(4),
  PMA = new_covariate(42),
  CR = new_covariate(0.5),
  CL_HEMO = new_covariate(0)
)

## Perform simulation
sim(
  ode = pkvancoanderson::model(),
  parameters = pkvancoanderson::parameters(),
  regimen = reg,
  covariates = covs
)
```

See [PKPDsim documentation](http://pkpdsim.insight-rx.com/) for more details
about how to set up model simulations.
