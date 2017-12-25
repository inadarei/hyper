It's quite common that we have an object that may have several attributes, but
one of the attributes is the "value" of the object. To solve for this common
situation is why the core vocabulaty defines the the h:value standard property.

##### h:value Usage Example

```json
{
  "product" : {
    "h:label" : "Box of Wine",
    "paid" : {
      "h:value" : "300",
      "currency" : "USD"
    }
  }
}
```
