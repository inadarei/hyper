### Attributes with pre-defined meanings

All of the pre-defined properties have keys in the
reserved "h:" namespace, and their meaning is defined as follows:

#### Name

There is actually no explicit property called "name" in Hyper, as you would see
in some other hypermedia types. Rather, the key pointing to an object
(from body, or another object)  is used as the "name" when translating
to/from the other media types.

#### h:link

  - optional.
  - Identical to the "links" attribute in the `head` section of the document,
    but applies in context, to an object that it is an attribute of.

#### h:label

  - optional.
  - "Some formats provide ways to give a human-readable label to an attribute.
    For example, where first_name is the attribute, "First Name" may be the
    label." ([Hypermedia Project
    Charter](https://github.com/the-hypermedia-project/charter/blob/master/reference/hypermedia-elements.md))

#### h:type

  - optional
  - "Used in several media types for pointing to outside semantics, such as
    Schema.org directly or an ALPS descriptor. This can be seen in documents
    that focus on linked data, such as JSON-LD and HTML+RDFa." ([Hypermedia
    Project
    Charter](https://github.com/the-hypermedia-project/charter/blob/master/reference/hypermedia-elements.md))

#### h:transclude

  - optional. true|false. Only valid in the context of a link object.
  - Hints to a client whether a link should be transcluded (e.g. image). If a
    linked resource should be transcluded, a client should determine the
    appropriate media type by inspecting the media-type returned by the call
    to the URI.
