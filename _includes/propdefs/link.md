h:link is a super-set of [h:ref](/spec#href) allowing representation of
complex hyperlinks and parametrized actions (similar to HTML's Form element).

h:link points to an array of objects, where each object can have following
properties of predefined semantic meaning:

###### uri

required. A [CURIE](https://www.w3.org/TR/2010/NOTE-curie-20101216/), a URI
[[RFC7320](https://tools.ietf.org/html/rfc7320)] or a URI Template
[[RFC6570](https://tools.ietf.org/html/rfc6570)].

###### template

if this field is present, the value of the uri attribute should be treated as a
URI Template [[RFC6570](https://tools.ietf.org/html/rfc6570)]. URI Template can
be CURIEd however. When present, the template attribute is an object containing
following properties:

1. `contentType` - a media-type that should be used to encode fields
      into, to satisfy the construction of a request.
      E.g. "application/x-www-form-urlencoded"

2. `fields` - an objects that explains what data
elements should be submitted to the endpoint represented by `uri`. Each
key is the name of the variable to be sent. If variables are going both
in URI template and in the body of the request, and disambiguiation is
required choose names sensibly to avoid conflicts. Each field object
can have following properties:
    1. `label` : optional. Hint for human-friendly label to present to humans,
        if an input form is rendered.
    1. `required` : optional. Whether a value is required. Boolean true/false.
        Default: true.
    1. `type` : optional. One of: "text", "number", "date", "hidden" or "boolean".
        Defaults to "text".
    1. `default` : optional. Default value.
    1. `pattern`: optional. Restrictions on allowed values. Syntax must be the
        same as used in [pattern in HTML5](https://www.w3.org/TR/2011/WD-html5-20110525/common-input-element-attributes.html#the-pattern-attribute)

3. `rel` - optional. array of link relation types per
    [RFC8288](https://tools.ietf.org/html/rfc8288). Only IANA-registered
    link relation types SHOULD be refered to by simple names, all
    application-specific and non-common link relation types should be URIs
    (usually CURRIEed, to save space).
4. `label` - optional. string. Usually human-readable, for presentation
    hints.
5. `action` - optional. string. Indicates the action represented by the uri
    transition. Hyper borrows definitions of possible action types from
    [UBER](http://www.uberhypermedia.org) and the list of valid values is as
    follows:

    1. `append` : An unsafe, non-idempotent request to add a new item. (e.g HTTP POST)
    2. `partial` : An unsafe, non-idempotent request to modify parts of an existing item. (e.g. HTTP PATCH)
    3. `read` : A safe, idempotent request. [DEFAULT] (e.g. HTTP GET)
    4. `remove` : An unsafe, idempotent request to delete an existing item. (e.g. HTTP DELETE)
    5. `replace` : An unsafe, idempotent request to replace an existing item. (e.g. HTTP PUT)

##### Example of an Advanced Link:

```json
{
  "h:link": [{
    "uri" : "http://api.example.com/users/{user}/?x={xval}&y=foo",
    "action" : "append",
    "template" : {
      "contentType" : "application/json",
      "fields" : {
        "user" : {"pattern" : "[a-z0-9_-]"},
        "xval" : {"type" : "number"},
        "firstName" : {}, "lastName" : {},
        "role" : {"required" : false}
      }
    }
  }]
}
```

Please note that "user" and "xval" fill-in values in the URI template, whereas
"firstname", "lastname" and "role" are going to be transmitted as JSON HTTP POST
Body elements.

##### An h:ref as h:link Example

As noted earlier, h:link is a superset of h:ref, any h:ref can actually be
represented as an h:link. Case in point: the [earier example](/spec#example-document-with-hrefs) of h:ref, when
represented as h:link would look as follows:

```json
{
  "h:head" {
    "title" : "Employees of North-East Department"
  },
  "department" : {
    "h:value" : "north-east",
    "h:label" : "North-East",
    "h:link" : [{"uri" : "http://api.example.com/departments/1234", "rel": "about"}]
  },
  "employees" : [

  ],
  "h:link" : [
    {"rel": "self",  "uri" : "http://api.example.com/users?dep=1234&page=4",
    {"rel": "next", "uri"  : "http://api.example.com/users?dep=1234&page=5",
    {"rel": "prev",  "uri" : "http://api.example.com/users?dep=1234&page=3",
    {"rel": "first", "uri" : "http://api.example.com/users?dep=1234&page=1",
    {"rel": "last",  "uri" : "http://api.example.com/users?dep=1234&page=10"
  ]
}
```
