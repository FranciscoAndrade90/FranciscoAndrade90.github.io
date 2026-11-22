---
title: "dsFedAte & dsFedAteClient"
excerpt: "Federated estimation of the Average Treatment Effect across multiple studies in DataSHIELD"
collection: software
date: 2026-11-13
---
A pair of [DataSHIELD](https://datashield.org) packages for estimating the average treatment effect (ATE) across several independent studies, such as randomised controlled trials, each held on its own data server. They implement in a federated way the g-formula estimator from "Federated Causal Inference: Multi-Study ATE Estimation beyond Meta-Analysis" (R. Khellaf, A. Bellet and J. Josse, 2025, [arXiv:2410.16870](https://doi.org/10.48550/arXiv.2410.16870)), including variance estimation. Each site returns only aggregate statistics, so individual-level data never leave their server.

The software follows DataSHIELD's client–server design:

- **dsFedAte** (server side) is installed on each data server (Opal or Armadillo). It computes the local ATE statistics and enforces DataSHIELD's disclosure controls. [CRAN](https://cran.r-project.org/package=dsFedAte)
- **dsFedAteClient** (client side) runs on the analyst's machine. It coordinates the analysis across the servers and combines their results through `ds.EstimateAte()`. [CRAN](https://cran.r-project.org/package=dsFedAteClient) ·
### Installation

```r
# On each data server
install.packages("dsFedAte")

# On the analyst's machine
install.packages("dsFedAteClient")
```

A full worked example is in the client package's vignette:

```r
vignette("federated_rct", package = "dsFedAteClient")
```

### Companion article

F. Andrade, R. Khellaf and J. Josse, "Federated Average Treatment Effect Estimation for Multi-Site RCTs with DataSHIELD", submitted to *Computo* (under review). [Read the article](https://franciscoandrade90.github.io/fedate-datashield/)

Joint work with Rémi Khellaf and Julie Josse.
