# Voter

A citizen sends two voter structures to a polling station, one with a vote public key and another one without a vote public key.
The polling station checks the validity of the vote.
If the citizen is allowed to vote, the polling station signs and publishes the voter structure which doesn't include the vote public key.
Otherwise, it signs and publishes the voter structure which includes the vote public key.
The polling station sends the publication to a publisher and also to the citizen.
If allowed to vote the citizen publishes her vote.

## Format

https://directdemocracy.vote/json-schema/0.0.1/voter.schema.json

## Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/voter.schema.json
key: station_public_key
signature: citizen_signature or station_signature
published: 1590298858399
expires: 1890298858399
referedum:
  key: referendum_public_key
  signagure: referendum_signature
citizen:
  key: citizen324_public_key
  signature: citizen324_signature
voteKey: vote_public_key
citizenSignature: citizen_signature
```
