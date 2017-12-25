Optional. Used to define a header of a Hyper message. Fields in the header section
apply to the entire message. There SHOULD be only one h:head property at the top
level. All subsequent h:head properties after the first one, or the ones at
deeper levels MUST be ignored.

h:head property points to a JSON object that MAY contain following optional
fields:

###### version

optional. Version property indicates the version of the `Hyper`
specification    that a message represents. Currently, there’s only one
version of the specification: 1.0, the current version. As such, the
version property, if present, MUST be set to 1.0, until there’s another
version of the specification. If the version field is ommited, it should be
assumed to be 1.0.

###### title

optional. Title of the document


###### hreflang

optional. ISO639-1 code of the language of the document. Defaults to ‘en’.

###### profiles

optional. A list of URIs. Each element of the list is a link
pointing to an ALPS profile that can provide additional semantic
information about the fields used in the document. If profiles provide
conflicting definitions, the last profile included overrides previous
definitions.

###### curies

optional. List of
[CURIEs](https://www.w3.org/TR/2010/NOTE-curie-20101216/), complying to the
W3C definition. In Hyper, CURIEs can be used in values of "uri" fields or
as any object's key's name. Please note that CURIEs can conflict with many
valid uris, such as the ones starting with prefixes like "mailto:", "git:",
"urn:", "about:" etc. When Hyper sees a colon (":") in a key name or in a
value of uri field, it considers the string to be a URI, unless it is a
CURIE registered in the document. Case in point: if you define a CURIE with
the prefix "data", you will stop otherwise legit URIs of the form "data:"
to be parsed as URIs, in your Hyper message. At which point you may want to
reconsider the prefix chosen. You can find the full list of possibly
conflicting prefixes by looking at the [IANA URI Schemes
Registry](https://www.iana.org/assignments/uri-schemes/uri-schemes.xhtml#uri-schemes-1).

**Important:** Hyper registers a special CURIE `{"prefix" : "h", "uri" :
"http://hyperjson.io/attributes/"}` that is always present and cannot
be removed or overriden.

##### Example use of h:head in a Hyper document:

```json
{
  "h:head": {
    "version": "1.0",
    "title": "Department Employees",
    "hreflang": "en",
    "profiles": ["ex:profiles/department-employees"],
    "curies": [{"prefix": "ex", "href": "http://api.example.com/"}],
  },
  "department" : {
    "name" : "North-East Region",
    "h:ref" : { "about" : "ex:regions/north-east"}
  }
}
```
