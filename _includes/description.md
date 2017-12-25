## Description

`Hyper` is a media type optimized for easy production and consumption of
hypermedia messages. Developers can write code against Hyper messages, and
by using implementations of the
[Representor](https://github.com/the-hypermedia-project/charter#representor-pattern)
pattern, such as [Kokua](https://github.com/inadarei/kokua) in Node, have their
messages become consumable in many popular hypermedia formats, such as: HAL,
Siren, UBER etc. Likewise, on the client side, you will be able to consume APIs
written in multiple formats, while only coding against Hyper:

![Hyper in Hub and Spoke](/img/hub-and-spoke.png)

Hyper allows implementations of the Representor pattern to leverage the [Hub
and
Spoke](http://www.enterpriseintegrationpatterns.com/ramblings/03_hubandspoke.html)
pattern and thus avoid the combinatorial explosion of complexity in the
alternative, point-to-point approach.

Due to its versatility, Hyper is also a very fine choice as the primary format of
an API, but it's entirely up to the API producer and the consumer whether they
choose to do that or translate Hyper to another format, such as HAL or UBER.
