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
trustee: trustee_public_key
area: https://nominatim.openstreetmap.org/?country=France&state=Bourgogne-Franche-Comté&county=Saône-et-Loire&city=Mâcon
title: my referendum
description: my description
question: do you agree?
answers: yes, no, abstain
deadline: 2020-12-15T20:00:00+00:00
website: https://www.myreferendum.net
```
