# vote

## format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.net/json-schema/1.0/vote.schema.json
title: vote
description: vote casted by a citizen for a referendum
type: object
required: [key, signature, published, referendum, answer]
properties:
  key:
    description: public key of the ballot
    type: string
    contentEncoding: base64
  signature:
    description: signature of the ballot
    type: string
    contentEncoding: base64
  published:
    description: date at which the vote was published
    type: string
    format: date-time
  referendum:
    description: public key of the referendum
    type: string
    contentEncoding: base64
  answer:
    description: answer to the question of the referendum
    type: string
```

## example

```yaml
key: ballot_public_key
signature: ballot_signature
published: 2020-01-12T20:20:02+00:00
referendum: public_key_of_referendum
answer: yes
```
