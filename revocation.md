# Revocation

## Description

Revocations are published by citizens to revoke their own card.
Then, they may create a new card with the same public key or a new public key.
Revocations are also published by citizens and truster to cancel endorsements they previously published.
It is useless to revoke a publication that already expired.
The expiration date of a revocation should match the one of the revoked publication.

## Format

https://directdemocracy.vote/json-schema/0.0.1/revocation.schema.json

## Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/revocation.schema.json
key: my_public_key
signature: my_signature
published: 2019-08-21T21:12:00+00.00
expires: 2022-08-21T21:12:00+00.00
revoked:
  key: public_key_of_the_card
  signature: signature_of_the_card
```
