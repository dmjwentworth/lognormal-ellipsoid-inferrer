# lognormal-ellipsoid-inferrer (logelin)
A tool which, by modelling the sampled galaxies as ellipsoids with intrinsic semi-axes drawn from a multivariate log-normal distribution, uses Bayesian inference to generate posteriors for parameters describing the underlying distribution of shapes and sizes of galaxies. 

Typically, a program such as Source Extractor will process telescope data, drawing ellipses around the projected shapes of distant galaxies, returning the semi-major and semi-minor axis lengths, $a$ and $b$, in arcseconds. In order to characterise the true scale of the galaxy the redshift must be used to calculate the angular diameter distance.

As such, this tool is designed to take these $a$ and $b$ values in arcseconds, along with the redshift for each galaxy, and then fit a Bayesian Hierarchical model, sampling the posterior distributions for the parameters which characterise the morphology of that particular sample of galaxies. 
