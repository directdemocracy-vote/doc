# Votes

## Description

Votes are published by [stations](station.md) once a [referendum](referendum.md) voting period is over.

## Format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.vote/json-schema/0.0.1/votes.schema.json
title: votes
description: list of votes used for a referedum by a station
type: object
required: [schema, key, signature, published, expires, referendum, citizen]
properties:
  schema:
    const: https://directdemocracy.vote/json-schema/0.0.1/votes.schema.json
  key:
    description: public key of the station
    type: string
    contentEncoding: base64
  signature:
    description: signature of the station
    type: string
    contentEncoding: base64
  published:
    description: date at which the votes were published
    type: string
    format: date-time
  expires:
    description: date at which the votes expire
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
  votes:
    description: list of votes
    type: array
    items:
      description: vote
      type: object
      required: [key, signature]
      properties:
        key:
          description: public key of the vote
          type: string
          contentEncoding: base64
        signature:
          description: signature of the vote
          type: string
          contentEncoding: base64
```

## Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/votes.schema.json
key: station_public_key
signature: station_signature
published: 2020-02-21T08:00:00+00:00
published: 2030-02-21T08:00:00+00:00
referendum:
  key: referendum_public_key
  signature: referendum_signature
votes:
- key: vote16_public_key
  signature: vote16_signature
- key: vote29_public_key
  signature: vote29_signature
- etc.
```
