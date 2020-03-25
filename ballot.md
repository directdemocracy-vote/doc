# Ballot

A citizen creates a ballot with empty `signature`, `station.refused` and `station.signature` fields.
The `signature` field is computed and filled in.
The `citizen.signature` field is computed and filled in.
The citizen then sends the ballot to the polling station.
The polling station checks the signatures and the validity of the ballot with the trustee of the referendum.
If the citizen is not allowed to vote, the polling station fills in the `station.refused` field with the reason why it was refused, signs it in `station.signature` and publishes the voter structure.
Such a publication means that the citizen attempted to vote, but failed, thus invalidating the public key of the vote.
Otherwise, the station removes the `citizen.public_key` and `citizen.signature` fields, signs and publishes the ballot.
Such a publication means that the citizen successfully voted for the referendum.
The polling station also sends its publication back to the citizen.
If allowed to vote the citizen publishes her [vote](vote.md).

Once the ballot is published, it can be verified by anyone.

## Format

https://directdemocracy.vote/json-schema/0.0.1/ballot.schema.json

## Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/ballot.schema.json
key: ballot_public_key
signature: ballot_signature
published: 1590298858399
expires: 1890298858399
referendum: referendum_public_key
station:
  key: station_public_key
  signature: station_signature_for_ballot (initially empty)
  refused: reason_why_the_ballot_was_refused_by_the_station (initially empty)
citizen:
  key: citizen_public_key
  signature: citizen_signature_for_ballot
```
