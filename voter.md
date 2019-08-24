# voter

## format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.net/json-schema/1.0/voter.schema.json
title: voter
description: citizen who voted in a referendum
type: object
required: [key, signature, published, referendum, citizen]
properties:
  key:
    description: public key of the station
    type: string
    contentEncoding: base64
  signature:
    description: signature of the station
    type: string
    contentEncoding: base64
  published:
    description: date at which the voter was published
    type: string
    format: date-time
  referendum:
    description: public key of the referendum
    type: string
    contentEncoding: base64
  citizen:
    description: public key of the citizen who voted at this referendum
    type: string
    contentEncoding: base64
```

## example

```yaml
key: station_public_key
signature: station_signature
published: 2019-11-23T21:21:33+00:00
referedum: referendum_public_key
citizen: citizen324_public_key
```
