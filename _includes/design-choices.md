### Design Choices

Primary purpose of Hyper (`application/vnd.hyper+json`) is to be used by
developers as the hypermedia type that they actually code against. As such,
simplicity and developer experience are very important in its design. Hyper
stays as close as possible to plain JSON and avoids being verbose or bloated
in its syntax.

Simplicity comes from an intentionally small set of additional constraints that
Hyper introduces on top of "plain old JSON". The Hyper spec is essentially as
short as the following three principles:

1. Hyper is a JSON document of arbitrary shape. Any JSON is a valid Hyper as
   long as it doesn't violate the other two rules (which most JSON documents,
   do not).
1. Keys of a Hyper document MAY be URIs. Such attributes indicate extra
   semantics and processing rules that MAY be provided by a resource at the
   other end of the URI. URIs do not have to be dereferenceable, however. They
   are just a namespace, and the meaning of a namespace CAN be provided by any
   convenient means (e.g. publishing an RFC, Swagger document or a nicely
   printed book). These URIs can also be Compact URIs -
   [CURIEs](https://www.w3.org/TR/2010/NOTE-curie-20101216/). Namespacing
   attributes by providing them as URIs is a primary way of introducing
   additional semantic and processing rules - foundation of extensibility in
   Hyper.
1. Applications producing and consuming Hyper messages acknowledge the implicit
   existence of a core set of extensions ('core vocabulary'), that is documented
   at a set of URIs, the root of which is <http://hyperjson.io/props/>.

Hyper allows gradual introduction of Hypermedia controls in the form of mixins.
As opposed to many hypermedia formats, there is no required object shape in
Hyper. Most valid JSON documents are also a valid Hyper documents. Additional
functionality is introduced through [extensions](#extensions). Extensions, in
Hyper, add functionality via mixins, rather than inheritance-style
implementation of a parent, abstract Hyper document. It is entirely up to
individual API developers to decide "how much" hypermedia they want to add to
their JSON payloads.

#### Default Mixin - Core Vocabulary

In Hyper, core vocabulary is mixed-in via the default extension. The default
extension is `{"prefix" : "h", "uri" : "http://hyperjson.io/props/"}` that is
always present and cannot be removed or overriden. Capabilities in the default
extension form a small but powerful vocabulary selected based on the guidelines
outlined in the [Hypermedia Project
Charter](https://github.com/the-hypermedia-project/charter/blob/master/reference/hypermedia-elements.md).

Hyper is a web standard, based on existing specifications, such as: URI
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
of URIs that all start with "<http://hyperjson.io/props/>". We can CURIE this URL
by defining a prefix such as: `{"h" : "http://hyperjson.io/props/"}` and then
long URIs like <http://hyperjson.io/props/ref> and
<http://hyperjson.io/props/link> become much simpler `h:ref` and `h:link`.
You can read more about CURIE standard at:
<https://www.w3.org/TR/2010/NOTE-curie-20101216/>

URI Template is a web standard that allows describing a range of Uniform
Resource Identifiers (URIs) through variable expansion. For instance
`http://api.example.com/users{user-id}/photo` can describe a template for how
a photo URI of any user may look in some API. You can read more about
URI templates in [RFC6570](http://tools.ietf.org/html/rfc6570)
