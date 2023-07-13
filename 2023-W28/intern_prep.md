### Stochastic Block Models for Cyber-Physical Systems

A cyber-physical system (CPS), like a power plant or water treatment plant, can be modeled as a set of networked sensors whose readings are correlated at any given point in time. To detect and localize anomalies, we can observe these sensor readings (and the correlations between them) and then look out for observations that depart from our expectations.

However, modeling the CPS as a fully-connected network is computationally expensive (quadratic in the number of sensors in the system), and unnecessary as the underlying physical system has a sparsely-connected structure. Existing graph-based anomaly detection techniques (e.g. [Graph Deviation Network][gdn]) can estimate a sparse structure, but cannot reason about the uncertainty of that estimate. For that, we need to be able to sample from a generative (random) model.

A stochastic block model (SBM) is a generative model of sparse random graphs that is parameterized by membership and block matrices that are of lower dimensionality than the full adjacency matrix. [`fastRG`][] is an efficient algorithm (linear in the number of edges) for sampling from this class of models. I am in the process of implementing `fastRG` as a [Pyro][pyro] distribution. Pyro is a probabilistic programing language (built on [PyTorch][torch]) which can learn parameters of probability distributions using a technique called [Stochastic Variational Inference][svi] (SVI).

Our stretch goal is to reimplement [GDN][gdn] using SBM+SVI, then train and test on the [WADI][wadi] dataset to see if we can produce some interesting results and visualizations using uncertainty estimates. We may not achieve this by the end of the internship, so we will start with the more tractable short-term goal of exploring and debugging my `fastRG` implementation by using SBM+SVI to infer the community structure of well-studied graphs like [Zachary's Karate Club][karate] or others in the [PyTorch Geometric][pyg] library.

[`fastRG`]: https://arxiv.org/pdf/1703.02998.pdf
[pyro]: https://pyro.ai/
[torch]: https://pytorch.org/
[svi]: https://pyro.ai/examples/intro_long.html
[karate]: https://en.wikipedia.org/wiki/Zachary%27s_karate_club
[gdn]: http://arxiv.org/pdf/2106.06947.pdf
[wadi]: https://itrust.sutd.edu.sg/itrust-labs_datasets/
[pyg]: https://pytorch-geometric.readthedocs.io/en/latest/modules/datasets.html
