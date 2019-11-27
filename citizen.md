# Citizen

## Description

A citizen is a unique person aged 18 or more.
Anybody can publish a citizen card to become a citizen.
The registration process requires the publication of a digitally signed citizen card with a family name, given names, picture, GPS location of home, etc.
No review or approval is needed.
However, the publisher of a citizen card won't be able to vote if her card is not endorsed by a reputed [truster](truster.md).
[Trusters](truster.md) will endorse cards they believe are correct.
Citizens should help [trusters](truster.md) by endorsing the cards of other citizens they personally know.

## Format

https://directdemocracy.vote/json-schema/0.0.1/citizen.schema.json

## Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/citizen.schema.json
key: citizen_public_key
signature: citizen_signature_for_citizen
published: 1590298858399
expires: 1890298858399
familyName: Smith
givenNames: John
picture: base64_encoded_jpeg_picture
latitude: 40724723
longitude: -73993403
```
