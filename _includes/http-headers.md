While Hyper doesn't mandate, expect or require usage of any specific HTTP
Headers, some HTTP headers provide important capabilities for processing any
hypermedia message. We left some important capabilities out of Hyper's core
vocabulary because they can be supported by said headers. Considering this,
we believe it is justified to discuss them in this spec, for the sake of the
completeness of the specification.

#### Profile

An HTTP header link [[RFC6906](https://tools.ietf.org/html/rfc5988#section-5)]
of profile [[RFC6906](https://tools.ietf.org/html/rfc6906)] link rel type. The
URI of the link SHOULD point to a resource that allows clients to learn about
additional semantics (constraints, conventions, extensions) that are associated
with Hyper document being processed. A great example of a such resource is an
[ALPS
document](https://tools.ietf.org/html/draft-amundsen-richardson-foster-alps-02).


##### Example Profile Link In An HTTP Header:

```
Link: <http://alps.io/documents/search>; rel="profile",
      <https://api.example.com/alps/app-specific>; rel="profile"
```

#### Content-Language

The human language or languages of the intended audience for the enclosed
content. See [[RFC3282](https://tools.ietf.org/html/rfc3282)] for more
information.
