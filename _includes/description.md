## Description

`Hyper` is a media type optimized for easy production and consumption of
hypermedia messages. Applications that leverage the
[Representor](https://github.com/the-hypermedia-project/charter#representor-pattern)
pattern - to communicate in multiple hypermedia formats - can code against
Hyper and let libraries like [Kokua](https://github.com/inadarei/kokua) do
the translations to and from a veriety of media types.

![Hyper in Hub and Spoke](/img/hub-and-spoke.png)

Hyper allows implementations of the Representor pattern to leverage the [Hub
and
Spoke](http://www.enterpriseintegrationpatterns.com/ramblings/03_hubandspoke.html)
pattern and thus avoid the combinatorial explosion of complexity in the
alternative, point-to-point approach.
