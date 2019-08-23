# endorsement

## description

Endorsements are used by citizens to endorse cards, referendums, anonymizers and trusters.
Endorsements are also used by trusters to endorse citizens, referendums, anonymizers and other trusters.
The algorithms used by trusters rely on publications, including endorsements, to generate their own endorsements.
Referendums and anonymizers should not generate endorsements.

## format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.net/json-schema/1.0/endorsement.schema.json
title: endorsement
description: claim that a participant (endorser) acknowledges another participant (endorsed)
type: object
required: [key, signature, published, citizen]
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
  endorse:
    description: public key of the endorsed participant
    type: string
    contentEncoding: base64
  revoke:
    description: if this field is set, the endorsement is revoked and the string should contain a justification for the revocation
    type: string
```

## example

```yaml
key: my_public_key
signature: my_signature
published: 2019-08-21T21:12:00+00.00
ciziten: public_key_of_the_endorsed_citizen
```
