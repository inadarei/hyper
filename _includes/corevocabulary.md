### Core Vocabulary

Despite its flexible and extensible nature, Hyper is a very simple
media type with a small vocabulary.

In Hyper, JSON arrays are used as sets, not ordered lists.  The
order of a specified array should not be considered part of the
conveyed information.

#### h:head

{% include propdefs/head.md %}

#### h:ref

{% include propdefs/ref.md %}

#### h:link

{% include propdefs/link.md %}

#### h:value

{% include propdefs/value.md %}

#### h:label

{% include propdefs/label.md %}

#### h:type

{% include propdefs/type.md %}

#### Name

There is actually no explicit property called "name" in Hyper, as you would see
in some other hypermedia types. Rather, the key pointing to an object (from
body, or another object)  is used as the "name" when translating to/from the
other media types.
