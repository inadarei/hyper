## Description

`Hyper` is a base media type for hypermedia messages. It is designed to capture
common aspects of a hypermedia message. Applications that leverage the
[Representor](https://github.com/the-hypermedia-project/charter#representor-pattern)
pattern - to produce and consume messages in multiple hypermedia types - can
code against Hyper, instead of a more specific message formats. Implementations of
the Representor pattern will translate from Hyper to more specific
hypermedia types and vice-versa.

![Hyper in Hub and Spoke](/img/hub-and-spoke.png)

Hyper allows implementations of the Representor pattern to leverage the [Hub
and
Spoke](http://www.enterpriseintegrationpatterns.com/ramblings/03_hubandspoke.html)
pattern and thus avoid the combinatorial explosion of complexity in the
alternative, point-to-point approach.
