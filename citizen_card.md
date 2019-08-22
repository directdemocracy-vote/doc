# citizen card

```yaml
$schema: http://json-schema.org/schema#
title: citizen card
type: object
required: [id, name, price]
properties
  id:
    type: number
    description: Product identifier
```

```yaml
identity:
  familyName: Smith
  givenName: John
  picture: base64_encoded_jpeg_picture
  latitude: 40.7247239
  longitude: -73.9934037
  birthday: 1970-12-31
  address:
    street: 21 2nd Avenue
    city: New York
    state: NY
    zip: 10003
    country: USA
key: my_public_key
signature: my_signature
```
