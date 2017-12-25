### Desing Choices

Primary purpose of Hyper (`application/vnd.hyper+json`) is to be used by developers
as the hypermedia type that they actually code against. As such, simplicity and
developer experience are very important in the design of Hyper. As much as Hyper
needs to be flexible and extensible, to capture the broadest range of hypermedia
use-cases, it cannot be verbose or bloated in its syntax. This foundational
principle of simplicity greatly influences the design of Hyper.

Hyper allows gradual introduction of Hypermedia controls in the form of mix-ins.
As opposed to many hypermedia formats, there is no required object shape in
Hyper. Any valid JSON is also a valid Hyper document. Additional functionality
is introduced through [extensions](#extensions). Extensions, in Hyper, add
functionality via mix-ins, rather than inheritance-style implementation of a
parent, abstract Hyper document. It is entirely up to individual API developers
to decide "how much" hypermedia they want to add to their JSON payloads.

#### Core Vocabulary

In Hyper, core vocabulary is mixed-in via the default extension. The default
extension is `{"prefix" : "h", "uri" : "http://hyperjson.io/props/"}` that is
always present and cannot be removed or overriden. Capabilities in the default
extension form a small but powerful vocabulary selected based on the guidelines
outlined in the [Hypermedia Project
Charter](https://github.com/the-hypermedia-project/charter/blob/master/reference/hypermedia-elements.md).

Hyper is a web standard, leveraging existing specifications, such as: URI
Template [[RFC6570](http://tools.ietf.org/html/rfc6570)],
[CURIEs](https://www.w3.org/TR/2010/NOTE-curie-20101216/) and [IANA-registered
Link Relation
Types](http://www.iana.org/assignments/link-relations/link-relations.xhtml).

#### CURIEs and URI Templates

CURIEs and URI Templates are used extensively in Hyper. If you are unfamiliar
with them, it is worth spending a minute explaining them.

CURIEs are just a standard way of abbreviating long URIs by assigning prefix to
the common part of the URI, similar to how namespaces are used in XML. If you
are using the same base URI repeatedly in your API, using CURIES can
significantly clean-up the payload and make it much more readable. Being a
hypermedia format, we use URIs extensively in Hyper so keeping things clean and
manageable is very useful.

Case in point: let's assume that we need to refer to a lot
of URIs that all start with "http://hyperjson.io/props". We can CURIE this URL
by defining a prefix such as: `{"h" : "http://hyperjson.io/props"}` and then
long URIs like `http://hyperjson.io/props/ref` and
`http://hyperjson.io/props/action` become much simpler `h:ref` and `h:action`.
You can read more about CURIE standard at:
<https://www.w3.org/TR/2010/NOTE-curie-20101216/>

URI Template is a web standard that allows describing a range of Uniform
Resource Identifiers (URIs) through variable expansion. For instance
`http://api.example.com/users{user-id}/photo` can describe a template for how
a photo URI of any user may look in some API. You can read more about
URI templates in [RFC6570](http://tools.ietf.org/html/rfc6570)
