### General Structure

Despite its flexible and extensible nature, Hyper is a very simple
media type with a small vocabulary.

Hyper has two main sections: "head" and "body". If you view a `Hyper` message as
encapsulating controls (links) and state, then `attributes` is where the state
resides. The meaning of each attribute depends on the
[profile](http://www.ietf.org/rfc/rfc6906.txt) of the document.

- `head` - contains properties relevant to the entire document.
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
     W3C definition. In Hyper, CURIEs can be used in "uri" fields or as any
     object's key. Please note that CURIEs can conflict with many valid uris, such
     as the ones starting with prefixes like "mailto:", "git:", "urn:", "about:"
     etc. When Hyper sees a colon (":") in a key or a URI, it considers the
     string to be a URI, unless it is a CURIE registered in the document. Case
     in point: if you define a CURIE with the prefix "data", you will stop
     otherwise legit URIs of the form "data:" to be parsed as URIs, in your
     message. At which point you may want to reconsider the prefix chosen. You
     can find the full list of possibly conflicting prefixes by looking at the
     [IANA URI Schemes
     Registry](https://www.iana.org/assignments/uri-schemes/uri-schemes.xhtml#uri-schemes-1).

      Hyper also registers a special CURIE `{"prefix" : "h", "uri" :
      "http://hyperjson.io/attributes.html"}` that is always present and cannot
      be removed or overriden.
  6. `links` - list of links relevant to the entire document. Each link object
  may have following properties:

      1. uri - required. string.
      2. rels - required. arraty of strings or URIs (usually CURRIEed)
      3. label - optional. string. Usually human-readable.

- `body` - required. Object. Contains the main payload of the message. Each
  property of the body object can be any valid JSON value (boolean, string,
  array or an object), but several fields that start with the reserved `h:`
  prefix, have pre-defined meanings.
