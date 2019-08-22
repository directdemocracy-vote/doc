# trust

## format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.net/json-schema/1.0/trust.schema.json
title: trust
description: trust attributed to a citizen card by a truster
type: object
required: [key, signature, citizen, trust, edited, validity]
properties:
  key:
    description: public key of the truster
    type: string
    contentEncoding: base64
  signature:
    description: signature of the trust by the truster
    type: string
    contentEncoding: base64
  citizen:
    description: public key of the trusted citizen
    type: string
    contentEncoding: base64
  trust:
    description: level of confidence of the truster on the existance of the citizen, uniqueness and accuracy of the citizen card
    type: number
    minimum: 0
  edited:
    description: date of the last modification or creation of the trust
    type: string
    format: date-time
  valididy:
    description: duration expressed in seconds after which this trust should be considered invalid
    type: integer
  comment:
    description: justification of the trust value
    type: string
```

## example

```yaml
key: truster_public_key
signature: truster_signature
citizen: citizen_public_key
trust: 0.89
edited: 2019-11-01T08:12:23+00:00
validity: 31577600
```
