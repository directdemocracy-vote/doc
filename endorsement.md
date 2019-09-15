# Endorsement

## Description

Endorsements are published by citizens or trustees to endorse various publications: citizens, referendums and organizations.
Trustees publish endorsements based on their expertise and deep analysis of many publications, including endorsements.

As a citizen, you should mainly endorse other citizens by reviewing and signing electronically their citizen card.
The review process is a questionnaire in which you will assess the accuracy of the information provided on the card.
If you answer yes to every question, you should endorse the citizen card.
Question includes: "Do you know well the person?" or "Did you meet physically the person recently?".
Like citizen cards, endorsements are published on the Internet so that everyone can see them.

### Revocations

A revocations is a special kind of endorsement meant to revoke a publication.
It has its `revocation` field set to `true`.
A revocation can be published by a citizen to revoke her own citizen card.
Then, she may create a new card with the same public key or a new public key.
Revocations are also published by citizens and trustees to distrust organizations, citizens or to cancel endorsements they previously published.
It is useless to revoke a publication that already expired.
The expiration date of a revocation should match the one of the revoked publication.

## Format

https://directdemocracy.vote/json-schema/0.0.1/endorsement.schema.json

## Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/endorsement.schema.json
key: my_public_key
signature: my_signature
published: 2019-08-21T21:12:00+00.00
expires: 2022-08-21T21:12:00+00.00
revoke: true
endorsed:
  key: public_key_of_the_card
  signature: signature_of_the_card
```
