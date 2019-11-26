# Referendum

## Description

A referendum is a [publication](publication.md) written by a citizen aiming at proposing a law at a specific political level: world, country, state, region, city, etc.
In case of a law conflict, the upper level law has always the priority over the lower level law.
For example, if a world law forbid the death penalty, then no lower level law (country, state, region, city, etc.) can allow it.
Once a referendum proposing a new law is accepted by a majority of voters, the corresponding law should be applied within the delay specified in the description of the referendum.

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
area: |
  city=Mâcon
  county=Saône-et-Loire
  state=Bourgogne-Franche-Comté
  country=France
  union=European Union
title: my referendum
description: my description
question: do you agree?
answers: |
  yes
  no
  abstain
deadline: 1590298858399
website: https://www.myreferendum.net
```
