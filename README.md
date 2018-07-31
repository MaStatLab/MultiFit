MultiFIT: Multivariate Multiscale Framework for Independence Tests
================================

Test for independence of two random vectors, learn and report the dependency structure. For more information, see Gorsky and Ma (2018) <arXiv:1806.06777>.

### Install
Package is available on CRAN,  <https://cran.r-project.org/web/packages/MultiFit/index.html> and may be installed on Linux and Mac using `devtools`:

```R
install.packages('devtools')
library('devtools')
devtools::install_github('MultiFit', 'MaStatLab')
```

### Example
Generate two 2x2 random vectors, x and y. The second margin of both are dependent, the first not. Run ```R multiFit``` to test for independence, run ```R multiSummary``` to report the detected dependency structure. See vignette for further detials and examples.

```R
set.seed(1)
n = 300
d1 = d2 = 2
x = matrix(0, nrow=n, ncol=d1)
y = matrix(0, nrow=n, ncol=d2)
x[,1] = rnorm(n)
x[,2] = runif(n)
y[,1] = rnorm(n)
y[,2] = sin(5*pi*x[,2]) + 1/5*rnorm(n)
fit = multiFit(x=x, y=y, verbose=TRUE)
w = multiSummary(x=x, y=y, fit=fit, alpha=0.0001)
```