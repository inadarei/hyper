An array of type indicators. a type indicator provides semantic information for
the object in context. It is very similar to the `rel` attribute of `h:link`,
but h:link indicates semantics of the linked element, whereas h:type indicates
semantics of the object in the context.

Just like in the case of `rels` you SHOULD only use standard types as simple
strings, all custom types should be indicated as CURIEd URIs.
