### Extensions

Hyper allows extending plain old JSON
[[RFC7159](https://tools.ietf.org/html/rfc7159)] through keys that are CURIEd
URIs. Most keys in your JSON payload have keys that are simple strings. They
only provide semantic meaning within the context of a particular message or an
application. In Hyper, the keys of JSON objects can also be CURIEd URIs and have
a meaning that is defined universally.

For instance, let's look at this simple Hyper document:

```json
{
  "firstname": "Laila", "lastname": "Stanton",
  "h:ref": {"profile": "http://example.com/users/2334"}
}
```

Looking at this message alone, given no other documentation, we cannot be
certain about the semantic meaning of "firstname" and "lastname" properties.
They are probably defined in an API documentation somewhere, or somehow other
communicated between the API producer and the consumer. However, knowing that
the message is a Hyper document, we can learn quite a bit about the `h:ref`
property:

1. It's a CURIE, with prefix "h".
2. In Hyper documents, "h" prefix is predefined and stands for
   `http://hyperjson.io/props/`, therefore the full URI form of `h:ref` key is:
   `http://hyperjson.io/props/ref`
3. Looking-up documentation at <http://hyperjson.io/props/ref> we can learn that
   this property defines a **hyperlink**, and can point to other APIs, web
   pages, files, locations within the same API, email addresses, or any other
   URI. Hyperlinks in Hyper documents are also required to define a
   [relationship
   type](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a#attr-rel)
   which "specifies the relationship of the target object to the link object"
