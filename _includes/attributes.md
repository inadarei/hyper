### Attributes with pre-defined meanings

All of the pre-defined properties have keys in the
reserved "h:" namespace, and their meaning is defined as follows:

#### Name

There is actually no explicit property called "name" in Hyper, as you would see
in some other hypermedia types. Rather, the key pointing to an object
(from body, or another object)  is used as the "name" when translating
to/from the other media types.

#### h:links

  - optional.
  - Identical to the "links" attribute in the `head` section of the document,
    but applies in context, to an object that it is an attribute of. It's an
    array of link objects, where each link object can have following attributes:

    1. `uri` - required. string. A CURIE, a URI or a URI Template per [RFC6570].
    2. `templated` - optional. Either boolean true or false. Defaults to "false" indicating
        that "uri" is not a templated URI and should be treated as a fully-qualified
        URI or a CURIED URI.
    3. `model` - required and only valid if "templated" == true. Contains an URI
       Template [RFC6570]-compliant string to be used to construct message
       bodies. Example: "name={firstName}&age={EmployeeAge}"
    4. `rels` - required. array of strings or URIs (usually CURRIEed)
    5. `label` - optional. string. Usually human-readable.
    6. `action` - optional. string. Indicates the action represented by the uri
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

  - optional
  - "Used in several media types for pointing to outside semantics, such as
    Schema.org directly or an ALPS descriptor. This can be seen in documents
    that focus on linked data, such as JSON-LD and HTML+RDFa." ([Hypermedia
    Project
    Charter](https://github.com/the-hypermedia-project/charter/blob/master/reference/hypermedia-elements.md))

#### h:transclude

  - optional. Allowed values: true or false. Only valid in the context of a link object.
  - Hints to a client whether a link should be transcluded (e.g. for an image).
    If a linked resource should be transcluded, a client should determine the
    appropriate media type by inspecting the media-type returned by a call to
    the corresponding URI.
