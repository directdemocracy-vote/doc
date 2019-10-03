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
title: my referendum
description: my description
question: do you agree?
answers:
- yes
- no
- abstain
deadline: 2020-01-31
areas:
- type: city
  name: Paris
  coords:
  - - x1
    - y1
    - x2
    - y2
    - etc.
  - - x1
    - y2
    - etc.
  - etc.
 - type: country
   name: Switzerland
trustees:
- trustee1_public_key
- trustee2_public_key
websites:
- https://www.myreferendum.com
- https://www.my-referendum.net
```
