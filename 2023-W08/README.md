### [Week of 2023-02-20]
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
Started a jupyter notebook [here](time-series-vae.ipynb).

#### Wednesday:
No commit today, too much work in progress. Trying to train a recurrent
autoencoder on audio data but it's very tricky. Will try more tomorrow.

#### Thursday/Friday:
Got a recurrent encoder/decoder setup akin to the one in the [ecg tutorial][ecg] training on audio data,
but it's not tuned right and just kind of spits out weird noise.
Maybe trying audio was a bit overly ambitious, but I still want to try a variational inference setup with pyro.

