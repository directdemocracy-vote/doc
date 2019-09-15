# Endorsement

## Description

Endorsements are published by citizens or trusters to endorse cards, referendums, stations and trusters.
The `endorsed.signature` field is necessary only when endorsing a card or a referendum.
It should not be set when endorsing a truster or a station.
Trusters publish endorsements based on their expertise and deep analysis of many publications, including endorsements.
Referendums and stations should not publish any endorsement.
Citizens and trusters can endorse any other participant.

As a citizen, you should mainly endorse other citizens by reviewing and signing electronically their card.
The review process is a questionnaire in which you will assess the accuracy of the information provided on the card.
If you answer yes to every question, you should endorse the card.
Question includes: "Do you know well the person?" or "Did you meet physically the person recently?".
Like cards, endorsements are published on the Internet so that everyone can see them.

### Revocations

Revocations are a special kind of endorsement meant to revoke a publication.
They have their `revocation` field set to `true`.
Revocations can be published by citizens to revoke their own citizen card.
Then, they may create a new card with the same public key or a new public key.
Revocations are also published by citizens and truster to distrust organizations, citizens or to cancel endorsements they previously published.
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
endorsed:
  key: public_key_of_the_card
  signature: signature_of_the_card
```
