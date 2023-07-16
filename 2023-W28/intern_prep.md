## Stochastic Block Models for Cyber-Physical Systems

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

### [Zachary's Karate Club][karate]

In 1977, an anthropologist named Wayne W. Zachary studied a 34-member karate club that split up during a conflict. By observing the relationships among the members, he was able to accurately predict which side of the schism they fell on. His dataset consists of a graph with 34 nodes, one for each member, and 78 undirected edges, one for each observed social relationship.

Zachary used a maximum-flow algorithm to predict the community structure, but we will use a stochastic block model with a 34x2 membership matrix (where each row represents the probabilities of a member belonging to each block) and a 2x2 block connection matrix (where each row represents the probabilities of a node within a block connecting to a node in the same block, or to a node in another block).

#### Exercises
[Pyro][pyro] has extensive documentation including a [detailed tutorial](https://pyro.ai/examples/intro_long.html). Read this tutorial before proceeding!

1. Using our SBM implementation, write a simple pyro model and guide to infer the membership and block matrices with maximum-likelihood estimation, and check the results against the ground truth.
2. Reparameterize the model to perform Bayesian regression. Try out different priors and compare the results.
3. Visualize the uncertainty in the Bayesian model's parameter estimates.
