# Voter

A citizen sends two voter structures to a polling station:
The first one has a `voteKey` field set to the public key of the vote and second one has no `voteKey` field.
The polling station checks the validity of the voter.
If the citizen is allowed to vote, the polling station signs and publishes the voter structure which doesn't include the `voteKey` field.
Otherwise, it signs and publishes the voter structure which includes the `voteKey` .
The polling station sends the publication to a publisher and also to the citizen.
If allowed to vote the citizen publishes her [vote](vote.md).

## Format

https://directdemocracy.vote/json-schema/0.0.1/voter.schema.json

## Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/voter.schema.json
key: station_public_key
signature: station_signature_for_voter (initially empty)
published: 1590298858399
expires: 1890298858399
citizenSignature: citizen_signature_for_voter
voteKey: vote_public_key (optional field)
referedum:
  key: referendum_public_key
  signagure: referendum_signature
citizen:
  key: citizen_public_key
  signature: citizen_signature
```
