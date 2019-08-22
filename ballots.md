# ballots

## format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.net/json-schema/1.0/ballots.schema.json
title: ballots
description: list of ballots used for a referedum by an anonymizer
type: object
required: [key, signature, published, referendum, citizen]
properties:
  key:
    description: public key of the anonymizer
    type: string
    contentEncoding: base64
  signature:
    description: signature of the anonymizer
    type: string
    contentEncoding: base64
  published:
    description: date at which the ballots were published
    type: string
    format: date-time
  referendum:
    description: public key of the referendum
    type: string
    contentEncoding: base64
  ballots:
    description: list of ballots
    type: array
    items:
      description: public key of the ballot
      type: string
      contentEncoding: base64
```

## example

```yaml
key: anonymizer_public_key
signature: anonymizer_signature
published: 2020-02-21T08:00:00+00:00
referendum: referendum_public_key
ballots:
- ballot16_public_key
- ballot29_public_key
- etc.
```
