# Voter

## Format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.vote/json-schema/0.0.1/voter.schema.json
title: voter
description: citizen who voted in a referendum
type: object
required: [schema, key, signature, published, expires, referendum, citizen]
properties:
  schema:
    const: https://directdemocracy.vote/json-schema/0.0.1/voter.schema.json
  key:
    description: public key of the station
    type: string
  signature:
    description: signature of the station
    type: string
  published:
    description: date at which the voter was published
    type: string
    format: date-time
  expires:
    description: date at which the voter expires
    type: string
    format: date-time
  referendum:
    type: object
    required: [key, signature]
    properties:
      key:
        description: public key of the referendum
        type: string
      signature:
        description: signature the referendum
        type: string
  citizen:
    type: object
    required: [key, signature]
    properties:
      key:
        description: public key of the citizen who voted at this referendum
        type: string
      signature:
        description: signature of the citizen who voted at this referendum
        type: string
```

## Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/voter.schema.json
key: station_public_key
signature: station_signature
published: 2019-11-23T21:21:33+00:00
expires: 2029-11-23T21:21:33+00:00
referedum:
  key: referendum_public_key
  signagure: referendum_signature
citizen:
  key: citizen324_public_key
  signature: citizen324_signature
```
