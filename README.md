# lognormal-ellipsoid-inferrer (`logelin`)

## About
A tool which, by modelling the sampled galaxies as ellipsoids with intrinsic semi-axes drawn from a multivariate log-normal distribution, uses Bayesian inference to generate posteriors for parameters describing the underlying distribution of shapes and sizes of galaxies. 

The main functionality, `logelin.infer.run_inference`, is designed to take the proper distance $a$ and $b$ values (kpc will usually be a suitable unit for galactic orders of magnitude), fit a Bayesian Hierarchical model, sampling the posterior distributions using an MCMC algorithm built into `numpyro` for the parameters which characterise the morphology of that particular sample of galaxies. 

Typically, a program such as Source Extractor will process telescope data, drawing ellipses around the projected shapes of distant galaxies, returning the semi-major and semi-minor axis lengths, $a$ and $b$, in arcseconds. In order to characterise the true scale of the galaxy, the redshift $z$ must be used to calculate the angular diameter distance. As such, the package includes a function to easily convert from angular extent to proper distance at a given red shift, accessed through `logelin.convert.arcsec_to_kpc`, which assumes a flat $\Lambda\rm{CDM}$ cosmology with parameters taken from the Planck 2018 collaboration, performing the calculations using `astropy`.


## Installation

Can be pip-installed: `pip install logelin`

## Limitations

Known to converge poorly in situations with high measurement error/small sample size. 

The incorporation of measurement error within `logelin.infer.model` can definitely be improved. Currently it assumes a flat error rate on proper $a$ and $b$. In real surveys however, we are likely to have detailed uncertainties on both the angular $a$ and $b$, as well as $z$.

Another issue arises when considering measurement error in `logelin.infer.model`. If `a_true` and `b_true` are sufficiently similar, it is not unlikely that after incorporating the measurement error that they get mixed up (`a_obs`<`b_obs`). I assume the most efficient way to achieve this would be creating a custom `numpyro` distribution that is derived from a bivariate uncorrelated Gaussian in `a_obs` and `b_obs`, except with the PDF being exactly $0$ in the region where `a_obs` < `b_obs`. 
