# Voter

A citizen creates a voter structure with empty `signature` and `station.signature` fields and without the `vote` field.
The `signature` field is computed and filled in.
The `vote` field is added with an empty `vote.signature` and `vote.refused` fields.
The `vote.signature` field is computed and filled in.
The citizen then sends the voter structure to the polling station.
The polling station checks the signatures and the validity of the voter with the trustee of the referendum.
If the citizen is not allowed to vote, the polling station fills in the `vote.refused` field with the reason why it was refused, signs and publishes the voter structure.
Such a publication means that the citizen attempted to vote, but failed, thus invalidating the public key of the vote.
Otherwise, it removes the `vote` field, signs and publishes the voter structure.
Such a publication means that the citizen successfully voted for the referendum.
The polling station also sends its publication back to the citizen.
If allowed to vote the citizen publishes her [vote](vote.md).

Once the voter structure is published, one can verify directly the station signature.
The citizen signature can be verified by emptying the `station.signature` and removing the vote field, if any.
The vote signature, if any, can be verified by emptying the `station.signature` and `vote.refused` fields.

## Format

https://directdemocracy.vote/json-schema/0.0.1/voter.schema.json

## Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/voter.schema.json
key: citizen1_public_key
signature: citizen1_signature_for_voter
published: 1590298858399
expires: 1890298858399
referendum:
  key: citizen2_public_key
  signature: citizen2_signature_for_referendum
station:
  key: station_public_key
  signature: station_signature_for_voter (initially empty)
vote:
  key: vote_public_key
  signature: vote_signature_for_voter
  refused: reason_why_the_vote_was_refused_by_the_station (initially empty)
```
