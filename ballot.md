# Ballot

See explanations [here](voting.md).

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
revoke: 0
```
