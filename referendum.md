# Referendum

## Description

A referendum is a [publication](publication.md) written by a citizen aiming at changing the law in a city, state, country or the whole world.
It should be published on the internet, so that everyone can see it.

## Format

https://directdemocracy.vote/json-schema/0.0.1/referendum.schema.json

## Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/referendum.schema.json
key: referendum_public_key
signature: referendum_signature
published: 2019-09-12T12:33:21+00:00
expires: 2029-09-12T12:33:21+00:00
trustee:
- trustee_public_key
areas:
- reference: https://nominatim.openstreemap.org
  type: city
  name: Paris
  latitude: 41.113295
  longitude: 6.054323 
- reference: https://nominatim.openstreemap.org
  type: country
  name: Switzerland
  latitude: 45.113295
  longitude: 6.554323 
title: my referendum
description: my description
question: do you agree?
answers:
- yes
- no
- abstain
deadline: 2020-12-15T20:00:00+00:00
website: https://www.myreferendum.net
```
