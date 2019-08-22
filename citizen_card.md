# citizen card

## format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.net/json-schema/1.0/citizen_card.schema.json
title: citizen card
description: information allowing to identify uniquely a citizen
type: object
required: [key, signature, edited, familyName, givenName, picture, latitude, longitude]
properties:
  key:
    description: public key of the citizen
    type: string
    contentEncoding: base64
  signature:
    description: signature of the identidy card by the citizen
    type: string
    contentEncoding: base64
  edited:
    description: date of the last modification or creation of the citizen card
    type: string
    format: date-time
  familyName:
    description: last name of the citizen
    type: string
  givenName:
    description: first name of the citizen
    type: string
  picture:
    description: photo of the citizen
    type: string
    contentEncoding: base64
    contentMediaType: image/jpeg
  latitude:
    description: latitude of the home of the citizen expressed in degrees
    type: number
    minimum: -90
    maximum: 90
  longitude:
    description: longitude of the home of the citizen expressed in degrees
    type: number
    minimum: -180
    maximum: 180
  id:
    description: national ID card number
    type: string
  passport:
    description: passport number
    type: string
  vote:
    description: national vote card number
    type: string
  driving:
    description: natioanl driving license number
    type: string
  insurance:
    description: national social insurance number
    type: string
  birthday:
    description: the birthday of the citizen
    type: string
    format: date
  sex:
    description: sex of the citizen: M for male, F for female, O for other
    type: string
    pattern: ^[MFO]$
  address:
    description: address of the home of the citizen
    type: object
    required: [street, city, country]
    properties:
      street:
        type: string
      city:
        type: string
      state:
        type: string
      zip:
        type: string
      country:
        type: string
```

# example:

```yaml
key: my_public_key
signature: my_signature
edited: 2019-08-02T20:20:39+00:00
familyName: Smith
givenName: John
picture: base64_encoded_jpeg_picture
latitude: 40.7247239
longitude: -73.9934037
passport: C03005988
birthday: 1970-12-31
address:
  street: 21 2nd Avenue
  city: New York
  state: NY
  zip: 10003
  country: USA
```
