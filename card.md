# Card

## Description

A card should identify uniquely a citizen.
Anybody can publish a card become a citizen.
The registration process requires that you publish a digitally signed card with your name, picture, GPS location of home, etc.
No review or approval is needed.
However, you won't be able to vote if your citizen card is not endorsed by a reputed [truster](truster.md).
[Trusters](truster.md) will endorse cards they believe are correct.
Citizens should help [trusters](truster.md) by endorsing the cards of other citizens they personally know.
Citizens should not publish cards with too much information, e.g., documents, address, sex, birthday, etc.
Rather, they should provide only information they agree to disclose publicly and that can be easily checked by others.
For example, it's easier and generally sufficient to publish a single document.
But publishing no document is perfectly fine as well.
Also, the address is really not needed since the latitude and longitude fields are more accurate and mandatory.

## Format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.vote/json-schema/0.0.1/card.schema.json
title: card
description: information allowing to identify uniquely a citizen
type: object
required: [schema, key, signature, edited, familyName, givenName, picture, latitude, longitude]
properties:
  schema:
    const: https://directdemocracy.vote/json-schema/0.0.1/card.schema.json
  key:
    description: public key of the citizen
    type: string
    contentEncoding: base64
  signature:
    description: signature of the card by the citizen
    type: string
    contentEncoding: base64
  published:
    description: date of publication of the citizen card
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
  documents:
    description: documents to be checked by citizen endorsers
    type: array
    items:
      type: object
      required: [type, issuer, number]
      properties:
        type:
          description: type of document (ID card, passport, vote card, driving license, insurance card)
          type: string
          pattern: ^id$|^passport$|^vote$|^driving$|^insurance$
        issuer:
          description: country or organization that issued the document and ensure the uniqueness of the citizen
          type: string
        number:
          description: number uniquely identifying the citizen
          type: string
  birthday:
    description: the birthday of the citizen
    type: string
    format: date
  sex:
    description: sex of the citizen
    type: string
    pattern: ^male$|^female$|^other$
  address:
    description: home address of the citizen
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

# Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/card.schema.json
key: my_public_key
signature: my_signature
published: 2019-08-02T20:20:39+00:00
familyName: Smith
givenName: John
picture: base64_encoded_jpeg_picture
latitude: 40.7247239
longitude: -73.9934037
document:
- type: passport
  issuer: USA
  number: C03005988
birthday: 1970-12-31
address:
  street: 21 2nd Avenue
  city: New York
  state: NY
  zip: 10003
  country: USA
```
