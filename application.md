Name : Irakli Nadareishvili
Email : irakli@gmail.com

Media type name: application
Media subtype name: vnd.hyper+json

Required parameters: n/a
Optional parameters : n/a

Encoding considerations : binary

Security considerations : Hyper+JSON shares security issues common to all JSON 
content types. See RFC 8259 Section #12 (https://trac.tools.ietf.org/html/rfc8259#section-12) 
for additional information.

This media type was designed to encode arbitrary data, therefore 
it may contain executable code, but it is entirely up to the implementation to
determine if the data is malicious and whether or not to execute it. Generally,
applications consuming Hyper+JSON documents should safeguard against possibility 
of malicious executible code to prevent attacks such as cross-site scripting (XSS).

Hyper+JSON heavily utilizes Uniform Resource Identifiers (URIs) and as such 
shares security issues common to URI usage.
See RFC3986 Section #7 (https://tools.ietf.org/html/rfc3986#section-7) 
for additional information.

Since Hyper+JSON can carry any type of data, some data may require privacy or 
integrity services. This specification does not prescribe any specific solution
and assumes that concrete implementations will utilize common, trusted approaches
such as TLS/HTTPS, OAuth2 etc.

Interoperability considerations : None

Published specification : http://hyperjson.io/spec.html

Applications which use this media : Various

Fragment identifier considerations :

Hyper+JSON follows RFC6901 for implementing URI Fragment Identification standard
to JSON content types.

Restrictions on usage : None

Provisional registration? (standards tree only) :
Registration is for vendor tree

Additional information :

1. Deprecated alias names for this type : n/a
2. Magic number(s) : n/a
3. File extension(s) : .json
4. Macintosh file type code : TEXT
5. Object Identifiers: n/a

General Comments:

Person to contact for further information :

1. Name : Irakli Nadareishvili
2. Email : irakli@gmail.com

Intended usage : Common. Hyper+JSON is a fully-featured hypermedia media type,
supporting all standard Hypermedia Factors. It can be used independently
or a as versatile intermediary media type for facilitating conversions between various
hypermedia types as described in the Representor
(https://github.com/the-hypermedia-project/charter#representor-pattern) pattern.


Author/Change controller : Irakli Nadareishvili.
