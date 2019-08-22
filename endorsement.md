# endorsement

## format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.net/json-schema/1.0/endorsement.schema.json
title: endorsement
description: claim that a citizen (endorser) acknowledges the accuracy and uniqueness of the citizen card of another citizen (endorsed)
type: object
required: [key, signature, published, citizen, trust]
properties:
  key:
    description: public key of the endorser
    type: string
    contentEncoding: base64
  signature:
    description: signature of the endorser
    type: string
    contentEncoding: base64
  published:
    description: date of publication of the endorsement
    type: string
    format: date-time
  citizen:
    description: public key of the endorsed citizen
    type: string
    contentEncoding: base64
  trust:
    description: level of confidence of the endorser on her acknowledgement
    type: number
    minimum: 0
    maximum: 1
  event:
    description: event justifying a very low trust
    type: string
    pattern: ^dead$|^moved$|^renamed$|^hacked$
  comment:
    description: justification of the trust value
    type: string
```

## example

```yaml
key: my_public_key
signature: my_signature
published: 2019-08-21T21:12:00+00.00
ciziten: public_key_of_the_endorsed_citizen
trust: 0.99
comment: he is my brother
```
