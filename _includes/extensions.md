### Extensions

Hyper allows extending plain old JSON
[[RFC7159](https://tools.ietf.org/html/rfc7159)] through keys that are CURIEd
URIs. Most keys in your JSON payload have keys that are simple strings. They
only carry semantic meaning within the context of a particular message or an
application. In Hyper, the keys of JSON objects can also be CURIEd URIs and have
a meaning that is defined more generally.

For instance, let's look at this simple Hyper document:

```json
{
  "firstname": "Laila", "lastname": "Stanton",
  "h:ref": {"profile": "http://example.com/users/2334"}
}
```

Looking at this message alone, given no other documentation, we cannot be certain
about the semantic meaning of "firstname" and "lastname" properties. They are
probably defined in an API documentation somewhere or somehow communicated between
the API producer and the consumer. However, knowing that this is a Hyper document,
we know following about the 'h:ref' property:

1. It's a CURIE, with prefix "h".
2. In Hyper, "h" prefix is predefined and stands for `http://hyperjson.io/attributes/`,
   therefore the full URI form of the key is: `http://hyperjson.io/attributes/ref`
3. Looking-up documentation at http://hyperjson.io/attributes/
