## Description

`Hyper` is a base media type for hypermedia messages. It is designed to capture
common aspects of a hypermedia message. Applications that leverage the
[Representor](https://github.com/the-hypermedia-project/charter#representor-pattern)
pattern - to produce and consume messages in multiple hypermedia types - can
code against Hyper, instead of a more specific message format. Implementations of
the Representor pattern will be able to translate from Hyper to more specific
hyper-media types and vice-versa.

![Hyper in Hub and Spoke](/img/hub-and-spoke.png)

Hyper media type allows implementations of the Representor to leverage the [Hub
and
Spoke](http://www.enterpriseintegrationpatterns.com/ramblings/03_hubandspoke.html)
pattern and this avoid the combinatorial explosion of complexity in the
alternative, point-to-point transformation.
