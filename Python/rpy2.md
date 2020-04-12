## rpy2

install: `conda install rpy2`

low-level: `rpy2.rinterface`

high-level: `rpy2.robjects`

### Importing packages

```python
import rpy2.robjects as robjects

from rpy2.robjects.packages import importr
# import R's "evir" package
base = importr('evir')
```

### Installing packages

install packages from the first mirror known to R

```python
# import rpy2's package module
import rpy2.robjects.packages as rpackages

# import R's utility package
utils = rpackages.importr('utils')

# select a mirror for R packages
utils.chooseCRANmirror(ind=1) # select the first mirror in the list
```

install packages using R’s own function install.package

```python
# R package names
packnames = ('ggplot2', 'hexbin')

# R vector of strings
from rpy2.robjects.vectors import StrVector

# Selectively install what needs to be install.
# We are fancy, just because we can.
names_to_install = [x for packnames if not rpackages.isinstalled(x)]
if len(names_to_install) > 0:
    utils.install_packages(StrVector(names_to_install))
```

### Getting R objects

```python
pi=robjects.r['pi']
pi[0]
>>> piplus2 = robjects.r('pi') + 2
>>> piplus2.r_repr()
c(3.14159265358979, 2)
>>> pi0plus2 = robjects.r('pi')[0] + 2
>>> print(pi0plus2)
5.1415926535897931
```

creating a R function

```python
robjects.r('''
        # create a function `f`
        f <- function(r, verbose=FALSE) {
            if (verbose) {
                cat("I am calling f().\n")
            }
            2 * pi * r
        }
        # call the function `f` with argument value 3
        f(3)
        ''')
```

