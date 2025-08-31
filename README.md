# lognormal-ellipsoid-inferrer (`logelin`)

## About
A tool which, by modelling the sampled galaxies as ellipsoids with intrinsic semi-axes drawn from a multivariate log-normal distribution, uses Bayesian inference to generate posteriors for parameters describing the underlying distribution of shapes and sizes of galaxies. 

The main functionality, `logelin.infer.run_inference`, is designed to take the proper distance $a$ and $b$ values (kpc will usually be a suitable unit for galactic orders of magnitude), fit a Bayesian Hierarchical model, sampling the posterior distributions using an MCMC algorithm built into `numpyro` for the parameters which characterise the morphology of that particular sample of galaxies. 

Typically, a program such as Source Extractor will process telescope data, drawing ellipses around the projected shapes of distant galaxies, returning the semi-major and semi-minor axis lengths, $a$ and $b$, in arcseconds. In order to characterise the true scale of the galaxy, the redshift $z$ must be used to calculate the angular diameter distance. As such, the package includes a function to easily convert from angular extent to proper distance at a given red shift, accessed through `logelin.convert.arcsec_to_kpc`, which assumes a flat $\Lambda\rm{CDM}$ cosmology with parameters taken from the Planck 2018 collaboration, performing the calculations using `astropy`.


## Installation


## Limitations
