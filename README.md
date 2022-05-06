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
