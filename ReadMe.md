Efficient Exact and Approximate Inference in Bayesian Networks
-----------

`SubGroupSeparation` is an R package for marginalization in Bayesian networks. It allows for efficient exact and approximate inference that works both in low- and high-dimensional settings. As illustrated below, efficient marginalization is reached by splitting the calculation into sub-calculations of lower dimensionality.

![SGS](https://github.com/cbg-ethz/SubGroupSeparation/blob/master/vignettes/figures/illustration.png?raw=true)

Installation
-----------

In order to install the package, it suffices to launch
`R CMD INSTALL path/to/SubGroupSeparation`
from a terminal, or `make install` from within the package source folder.

Being hosted on GitHub, it is possible to use the `install_github`
tool from an R session:

```{r eval=FALSE}
library("devtools")
install_github("cbg-ethz/SubGroupSeparation")
```

`SubGroupSeparation` requires R `>= 3.5`, and depends on
`bitops` and
`methods`. Other packages are requested in
order to plot graphs, but are not mandatory.

Reference
---------
If you use `SubGroupSeparation` in your work, please cite it as:
```
Fritz M. Bayer, Giusi Moffa, Niko Beerenwinkel, Jack Kuipers. "Marginalization in Bayesian Networks: Integrating Exact and Approximate Inference" arXiv preprint, 2021
```

Demonstration 
-------------

```{r eval=FALSE}
library(SubGroupSeparation)
library(reshape2)

# create BN and label variables 
set.seed(6)
myBayesNet <- randomBN(3)
myBayesNet@variables <- c("rain", "sprinkler", "wet grass")
plot(myBayesNet)

# what's the probability of having rain and wet grass at the same time?
# define observed variables and calculate marginal probability
myObserved <- list(observed.vars=c("rain", "wet grass"), observed.vals=c(2,2))
exactInference(myBayesNet,myObserved)

```
