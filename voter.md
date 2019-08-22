# voter

## format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.net/json-schema/1.0/voter.schema.json
title: voter
description: citizen who voted in a referendum
type: object
required: [key, signature, referendum, citizen]
properties:
  key:
    description: public key of the anonymizer
    type: string
    contentEncoding: base64
  signature:
    description: signature of the anonymizer
    type: string
    contentEncoding: base64
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
key: anonymizer_public_key
signature: anonymiser_signature
referedum: referendum_public_key
citizen: citizen324_public_key
```
