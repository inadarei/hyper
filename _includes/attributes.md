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
    but applies in context, to an object that it is an attribute of. It's an
    array of link objects, where each link object can have following attributes:

    1. `uri` - required. A
        [CURIE](https://www.w3.org/TR/2010/NOTE-curie-20101216/), a URI
        [[RFC7320](https://tools.ietf.org/html/rfc7320)] or a URI Template
        [[RFC6570](https://tools.ietf.org/html/rfc6570)].
    2. `template` - if this field is present, the value of the uri attribute
        should be treated as a URI Template
        [[RFC6570](https://tools.ietf.org/html/rfc6570)]. URI Template can be
        CURIEd however. When present, the template attribute is an object
        containing following properties:

          1. `contentType` - a media-type that should be used to encode fields
                into, to satisfy the construction of a request.
                E.g. "application/x-www-form-urlencoded"

          2. `fields` - an objects that explains what data
          elements should be submitted to the endpoint represented by `uri`. Each
          key is the name of the variable to be sent. If variables are going both
          in URI template and in the body of the request, and disambiguiation is
          required (there's variable with the same name required in both URI
          and the body), a "uri:" template can be used. Each field object
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

          example:

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

          Please note that "user" and "xval" fill-in values in the URI template,
          whereas "firstname", "lastname" and "role" are going as JSON HTTP POST
          Body elements.

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

#### h:label

  - optional.
  - "Some formats provide ways to give a human-readable label to an attribute.
    For example, where first_name is the attribute, "First Name" may be the
    label." ([Hypermedia Project
    Charter](https://github.com/the-hypermedia-project/charter/blob/master/reference/hypermedia-elements.md))

#### h:type

  - optional. Array of type indicators.
  - a type indicator provides semantic information for the object in context. It
    is very similar to the `rel` attribute of `h:link`, but h:link indicates
    semantics of the linked element, where h:type indicates semantics of the
    object in the context.

#### h:transclude

  - optional. Allowed values: true or false. Only valid in the context of a link object.
  - Hints to a client whether a link should be transcluded (e.g. for an image).
    If a linked resource should be transcluded, a client should determine the
    appropriate media type by inspecting the media-type returned by a call to
    the corresponding URI.
