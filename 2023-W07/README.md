### [Week of 2023-02-13]
I got access to OIT research cluster, and set up and run the [pyro][]
example about [variational autoencoders][vae]
on MNIST to play with making inferences about the autoencoder's latent variables.

Austen suggested feeding the autoencoder random data to see how it affects
the distribution of latent samples, but I haven't tried this yet.

We also discussed setting up the problem for public time-series datasets
with known results.
We found this [tutorial using heart monitor data][ecg] and also this
anomaly detection [benchmark suite][nab].

[pyro]: http://pyro.ai
[vae]: https://pyro.ai/examples/vae.html
[ecg]: https://curiousily.com/posts/time-series-anomaly-detection-using-lstm-autoencoder-with-pytorch-in-python/
[nab]: https://github.com/numenta/NAB


