# Endorsement

## Description

Endorsements are published by citizens or trusters to endorse cards, referendums, stations and trusters.
If set, the `revoke` field means that any previous endorsement of the same participant should be disregarded.
A citizen can endorse her own card with a revoke field set to publicly discard it.
Then, she may create a new card with the same public key or a new public key.
The `endorsed.signature` field is necessary only when endorsing a card or a referendum.
It should not be set when endorsing a truster or a station.
Trusters publish endorsements based on their expertise and deep analysis of many publications, including endorsements.
Referendums and stations should not publish any endorsement.

## Format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.net/json-schema/1.0/endorsement.schema.json
title: endorsement
description: claim that a participant (endorser) acknowledges another participant (endorsed)
type: object
required: [key, signature, published, endorsedKey]
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
  endorsed:
    required: [key]
    properties:
      key:
        description: public key of the endorsed participant
        type: string
        contentEncoding: base64
      signature:
        description: signature of a card, endorsement or referendum
        type: string
        contentEncoding: base64
  revoke:
    description: if this field is set, the endorsement is revoked and the string should contain a justification for the revocation
    type: string
```

## Example

```yaml
key: my_public_key
signature: my_signature
published: 2019-08-21T21:12:00+00.00
endorsed:
  key: public_key_of_the_card
  signature: signature_of_the_card
```
