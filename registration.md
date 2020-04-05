# Registration

After she received a signed accepted [ballot](ballot.md) from the station, the citizen creates a registration structure and sends it to the [station](station.md).
The `station.signature` field is left empty.
The `signature` field is computed and filled in.
The citizen then sends the registration to the [station](station.md).
The station checks the signatures of the registration and if correct, sign it and publish it.
Such a publication means that the citizen successfully voted for the referendum at the station.
The polling station also sends this publication back to the citizen.
The citizen can then publish her [vote](vote.md).

Once the registration is published, it can be verified by anyone.

## Format

https://directdemocracy.vote/json-schema/0.0.1/registration.schema.json

## Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/ballot.schema.json
key: citizen_public_key
signature: registration_signature_by_citizen
published: 1590298858399
expires: 1890298858399
referendum: referendum_public_key
station:
  key: station_public_key
  signature: station_signature_for_registration (initially empty)
```
