# endorsement

## format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.net/json-schema/endorsement.schema.json
title: endorsement
description: claim that a citizen (endorser) acknowledges the accuracy and uniqueness of the citizen card of another citizen (endorsed)
type: object
required: [citizen, trust, edited, key, signature]
properties:
  citizen:
    description: public key of the endorsed citizen
    type: string
    contentEncoding: base64
  trust:
    description: level of confidence of the endorser on her acknowledgement
    type: number
    minimum: 0
    maximum: 1
  edited:
    description: date of the last modification or creation of the citizen card
    type: string
    format: date-time
  key:
    description: public key of the citizen
    type: string
    contentEncoding: base64
  signature:
    description: signature of the identidy card by the citizen
    type: string
    contentEncoding: base64
  comment:
    description: justification of the trust value
    type string
```

## example

```yaml
ciziten: public_key_of_the_endorsed_citizen
edited: 2019-08-21T21:12:00+00.00
trust: 0.99
key: my_public_key
signature: my_signature
comment: he is my brother
```
