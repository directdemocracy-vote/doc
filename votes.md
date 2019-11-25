# Votes

## Description

Votes are published by [stations](station.md) once a [referendum](referendum.md) voting period is over.

## Format

https://directdemocracy.vote/json-schema/0.0.1/votes.schema.json

## Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/votes.schema.json
key: station_public_key
signature: station_signature
published: 1590298858399
published: 1890298858399
referendum:
  key: referendum_public_key
  signature: referendum_signature
votes:
- key: vote16_public_key
  signature: vote16_signature
- key: vote29_public_key
  signature: vote29_signature
- etc.
```
