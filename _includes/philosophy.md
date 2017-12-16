### Philosophy

Primary purpose of Hyper (`application/vnd.hyper`) is to be used by developers
as the hypermedia type that they actually code against. As such, developer
experience is very important. As much as Hyper needs to be flexible and generic
enough to capture the broadest range of hypermedia use-cases, it cannot be
verbose or bloated in its syntax, since we don't intend there to be any
additional translation between developer's code and Hyper - Hyper is the
translation layer. This foundational principle greatly affects the design of
Hyper.

To achieve wide compatibility with broade range of hypermedia types, Hyper
follows the guidelines outlined in the [Hypermedia Project
Charter](https://github.com/the-hypermedia-project/charter/blob/master/reference/hypermedia-elements.md).

Hyper leverages existing standards, such as: [URI Template
[RFC6570]](http://tools.ietf.org/html/rfc6570), [CURIEs](https://www.w3.org/TR/2010/NOTE-curie-20101216/) and
[IANA-registered Link Relation
Types](http://www.iana.org/assignments/link-relations/link-relations.xhtml).
