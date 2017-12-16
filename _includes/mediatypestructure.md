### General Structure

Despite its flexible and extensible nature, Hyper is a very simple
media type with a small vocabulary.

Hyper has two main sections: "meta" and "body". If you view a `Hyper` message as
encapsulating controls (links) and state, then `attributes` is where the state
resides. The meaning of each attribute depends on the
[profile](http://www.ietf.org/rfc/rfc6906.txt) of the document.

- `meta` - contains properties relevant to the entire document.
  1. `version` - optional. Version property indicates the version of the `Hyper`
     specification that a message represents. Currently, there’s only one
     version of the specification: 1.0, the current version. As such, the
     version property, if present, MUST be set to 1.0, until there’s another
     version of the specification. If the version field is ommited, it should be
     assumed to be 1.0.
  2. `title` - optional. Title of the document
  3. `hreflang` - optional. ISO639-1 code of the language of the document. Defaults to ‘en’.
  4. `profiles` - optional. A list of URIs. Each element of the list is a link
     pointing to an ALPS profile that can provide additional semantic
     information about the fields used in the document. If profiles provide
     conflicting definitions, the last profile included overrides previous
     definitions.
  5. `curies` - optional. List of
     [CURIEs](https://www.w3.org/TR/2010/NOTE-curie-20101216/), complying to the
     W3C definition.
  6. `links` - list of links relevant to the entire document. Each link object
  may have following properties:

      1. uri - required. string.
      2. rels - required. arraty of strings or URIs (usually CURRIEed)
      3. label - optional. string. Usually human-readable.

- `body` - required. Object. Contains the main payload of the message. Each
  property of the body object points to a `$Property` object. The $Property
  object is a core element of the Hyper mediatype that can be used recursively. We
  explain it in detail, below in this specification.

  Please note that, unlike the core types in some other hypermedia formats,
  there is no explicit property called “name” in $Property. Rather, the key of
  pointing to a $Property object (from body, or another $Property) is used as
  the “name” value. We find that this approach leads to much more idiomatic
  and less annoyingly verbose JSON.
