Points to a JSON object where keys are link relationship types and values are
corresponding URIs.

##### Example Document with h:refs:

```json
{
  "h:head" {
    "title" : "Employees of North-East Department"
  },
  "department" : {
    "h:value" : "north-east",
    "h:label" : "North-East",
    "h:ref" : {"about" : "http://api.example.com/departments/1234"}
  },
  "employees" : [

  ],
  "h:ref" : {
    "self"  : "http://api.example.com/users?dep=1234&page=4",
    "next"  : "http://api.example.com/users?dep=1234&page=5",
    "prev"  : "http://api.example.com/users?dep=1234&page=3",
    "first" : "http://api.example.com/users?dep=1234&page=1",
    "last"  : "http://api.example.com/users?dep=1234&page=10"
  }
}
```
