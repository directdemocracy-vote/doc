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
published: 1574679658399
expires: 1890298858399
trustee: trustee_public_key
area: https://nominatim.directdemocracy.vote/?world=Earth&union=European Union&country=France&state=Bourgogne-Franche-Comté&county=Saône-et-Loire&city=Mâcon
title: my referendum
description: my description
question: do you agree?
answers: yes, no, abstain
deadline: 1590298858399
website: https://www.myreferendum.net
```
