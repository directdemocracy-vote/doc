# Citizen

## Description

A citizen is a unique person aged 18 or more.
Anybody can publish a citizen card to become a citizen.
The registration process requires the publication of a digitally signed citizen card with a family name, given names, picture, GPS location of home, etc.
No review or approval is needed.
However, the publisher of a citizen card won't be able to vote if her card is not endorsed by a reputed [truster](truster.md).
[Trusters](truster.md) will endorse cards they believe are correct.
Citizens should help [trusters](truster.md) by endorsing the cards of other citizens they personally know.
Citizens should not publish cards with too much information, e.g., documents, address, sex, birthday, etc.
Rather, they should provide only information they agree to disclose publicly and that can be easily checked by others.
For example, it's easier and generally sufficient to publish a single document.
But publishing no document is perfectly fine as well.
Also, the address is really not needed since the latitude and longitude fields are more accurate and mandatory.

## Format

https://directdemocracy.vote/json-schema/0.0.1/citizen.schema.json

## Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/citizen.schema.json
key: my_public_key
signature: my_signature
published: 2019-08-02T20:20:39+00:00
expires: 2029-08-02T20:20:39+00:00
familyName: Smith
givenNames: John
picture: base64_encoded_jpeg_picture
latitude: 40724723
longitude: -73993403
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
