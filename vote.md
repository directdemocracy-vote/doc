# Vote

## Format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.vote/json-schema/0.0.1/vote.schema.json
title: vote
description: vote casted by a citizen for a referendum
type: object
required: [schema, key, signature, published, expires, referendum, answer]
properties:
  schema:
    const: https://directdemocracy.vote/json-schema/0.0.1/vote.schema.json
  key:
    description: public key of the vote
    type: string
    contentEncoding: base64
  signature:
    description: signature of the vote
    type: string
    contentEncoding: base64
  published:
    description: date at which the vote was published
    type: string
    format: date-time
  expires:
    description: date at which the vote expires
    type: string
    format: date-time
  referendum:
    type: object
    required: [key, signature]
    properties:
      key:
        description: public key of the referendum
        type: string
        contentEncoding: base64
      signature:
        description: signature of the referendum
        type: string
        contentEncoding: base64
  answer:
    description: answer to the question of the referendum
    type: string
```

## Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/vote.schema.json
key: vote_public_key
signature: vote_signature
published: 2020-01-12T20:20:02+00:00
expires: 2030-01-12T20:20:02+00:00
referendum:
  key: public_key_of_the_referendum
  signature: signature_of_the_referendum
answer: no
```
