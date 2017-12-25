### Extensions

Hyper allows extending plain old JSON
[[RFC7159](https://tools.ietf.org/html/rfc7159)] through keys that are CURIEd
URIs. Most keys in your JSON payload have keys that are simple strings. They
only carry semantic meaning within the context of a particular message or an
application. In Hyper, the keys of JSON objects can also be CURIEd URIs and have
a meaning that is defined more generally.

For instance, let's look at this simple Hyper document:

```JSON
{
  "firstname": "Laila", "lastname": "Stanton",
  "h:ref": {"profile": "http://example.com/users/2334"}
}
```


semantic
meaning specific to the message or a particular application, but communicating
parties can introduce shared semantic knowledge by
