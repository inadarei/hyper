### Philosophy

Primary purpose of Hyper (`application/vnd.hyper+json`) is to be used by developers
as the hypermedia type that they actually code against. As such, simplicity and
developer experience are very important in the design of Hyper. As much as Hyper
needs to be flexible and extensible, to capture the broadest range of hypermedia
use-cases, it cannot be verbose or bloated in its syntax. This foundational
principle of simplicity greatly influences the design of Hyper.

Hyper allows gradual introduction of Hypermedia controls in the form of mix-ins.
As opposed to many hypermedia formats, there is no required shape in Hyper. Any
valid JSON is also a valid Hyper document. Additional functionality is
introduced through [extensions](#extensions). It is entirely up to API
developers to decide "how much" hypermedia they want to add to their JSON
payloads.

In Hyper, default set of additional semantics is mixed-in via a default
extension (`{"prefix" : "h", "uri" : "http://hyperjson.io/attributes/"}`) that
is always present and cannot be removed or overriden. Capabilities in the
default extension are selected based on the guidelines outlined in the
[Hypermedia Project Charter](https://github.com/the-hypermedia-project/charter/blob/master/reference/hypermedia-elements.md).

Hyper is a web standard, leveraging existing specifications, such as: [URI
Template [RFC6570]](http://tools.ietf.org/html/rfc6570),
[CURIEs](https://www.w3.org/TR/2010/NOTE-curie-20101216/) and [IANA-registered
Link Relation
Types](http://www.iana.org/assignments/link-relations/link-relations.xhtml).
