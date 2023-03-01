# basilisk-journal

### [Week of 2023-02-13](/2023-02-13/)
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


### [Week of 2023-02-20](/2023-02-20/)
#### Monday:
Set up this repository. Found another example in the pyro documentation that I
want to run through, this one about [forecasting time series data][forecast]. It might
be a good springboard to build from. Would be interesting to compare results with
the benchmarks/tutorials above.

Also, there are lots and lots of academic papers and online tutorials about
the topic of time-series anomaly detection in a variety of domains. 
I've started a reference list in Zotero.

[forecast]: https://pyro.ai/examples/forecasting_i.html

#### Tuesday:
Read the [forecast][] tutorial a little more. There's a lot of complexity there so for the moment I'll
stick with SVI for a time-series recurrent autoencoder.
Started a jupyter notebook [here](/2023-02-20/time-series-vae.ipynb).

#### Wednesday:
No commit today, too much work in progress. Trying to train a recurrent
autoencoder on audio data but it's very tricky. Will try more tomorrow.

#### Thursday/Friday:
Got a recurrent encoder/decoder setup akin to the one in the [ecg tutorial][ecg] training on audio data,
but it's not tuned right and just kind of spits out weird noise.
Maybe trying audio was a bit overly ambitious, but I still want to try a variational inference setup with pyro.

### Week of 2023-02-27
#### Monday:
The OIT research cluster has been down for a few days, but Panayot directed me to Google Colab for compute resources.
I've made a project folder on Drive (accessible to people with PSU login):
[https://drive.google.com/drive/folders/13XwYUAvBC_IpcdwvJAtclBsRxD7b2mT2?usp=sharing]

#### Tuesday:
I was given the link to the [RTS-GMLC repository](https://github.com/GridMod/RTS-GMLC) which contains
lots of real-time power grid data. I've only started to sift through it. This also helped me contextualize
[this repository](https://github.com/Gombessa1938/llnl_summer) from a previous student, which contains
models for some of this power grid data.

#### Wednesday:
Sifted through the RTS-GMLC data a little more. I will try to make a slide deck w/figures to
organize my thoughts about where to go from here.
