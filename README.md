pyflann3
========

NOTA BENE
---------

This is currently a work in progress. If this works out of the box, good. Otherwise it would be worth noting that it's work in progress.

Introduction
------------

This is a fork of the abandoned [pyflann](https://github.com/primetang/pyflann) project, which is a Python wrapper for
Marius Muja's excellent [FLANN - Fast Library for Approximate Nearest Neighbors](http://www.cs.ubc.ca/research/flann/).

Improvements over the original project:

1. Python 3.x compatibility.
2. Pre-built libraries bundled are optimized with the Intel compiler and performance libraries.

Installation
------------

Packages are not provided via PyPI, for the following reasons:

1. Intel library dependencies.
2. To prevent pollution of PyPI with half baked, abandoned forks.
3. Pre-built binaries only have 64-bit support.

    git clone https://github.com/cynthia/pyflann3.git
    pip install -e pyflann3

Examples
--------

Examples have been taken from the original documentation:

```python
from pyflann import *
import numpy as np

dataset = np.array(
    [[1., 1, 1, 2, 3],
     [10, 10, 10, 3, 2],
     [100, 100, 2, 30, 1]
     ])
testset = np.array(
    [[1., 1, 1, 1, 1],
     [90, 90, 10, 10, 1]
     ])
flann = FLANN()
result, dists = flann.nn(
    dataset, testset, 2, algorithm="kmeans", branching=32, iterations=7, checks=16)
print(result)
print(dists)

dataset = np.random.rand(10000, 128)
testset = np.random.rand(1000, 128)
flann = FLANN()
result, dists = flann.nn(
    dataset, testset, 5, algorithm="kmeans", branching=32, iterations=7, checks=16)
print(result)
print(dists)
```
