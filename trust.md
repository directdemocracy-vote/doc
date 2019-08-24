# trust

## format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.net/json-schema/1.0/trust.schema.json
title: trust
description: trust attributed to a citizen card by a truster
type: object
required: [key, signature, published, citizen, validity]
properties:
  key:
    description: public key of the truster
    type: string
    contentEncoding: base64
  signature:
    description: signature of the trust by the truster
    type: string
    contentEncoding: base64
  published:
    description: date of publication of the trust
    type: string
    format: date-time
  citizen:
    description: public key of the trusted citizen
    type: string
    contentEncoding: base64
  valididy:
    description: duration expressed in seconds after which this trust should be considered invalid
    type: integer
```

## example

```yaml
key: truster_public_key
signature: truster_signature
published: 2019-11-01T08:12:23+00:00
citizen: citizen_public_key
validity: 31577600
```
