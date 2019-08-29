# Referendum

## Description

A referendum is a [publication](publication.md) written by an [author](author.md) aiming at changing the law in a city, state, country or the whole world.
It should be published on the internet, so that everyone can see it.

# Format

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://directdemocracy.vote/json-schema/1.0.0/referendum.schema.json
title: referendum
description: referendum proposing a new law or a change in some existing law
type: object
required: [key, signature, published, title, description, question, answers, deadline, areas, trusters]
properties:
  key:
    description: public key of the author of the referendum
    type: string
    contentEncoding: base64
  signature:
    description: signature of the author of the referendum
    type: string
    contentEncoding: base64
  published:
    description: date of the publication of the referendum
    type: string
    format: date-time
  title:
    description: title of the referendum
    type: string
  description:
    description: detailed description of the referendum (markdown allowed)
    type: string
  question:
    description: question to which the citizen should answer
    type: string
  answers:
    description: possible answers to the above question, typically, yes, no, abstain
    type: array
    items:
      type: string
  deadline:
    type: string
    format: date-time
  areas:
    description: areas in which the citizen should live to vote for this referendum
    type: array
    items:
      type: object
      description: area
      properties:
        type:
          description: type of area (city, department, state, county, country, etc.)
          type: string
        name:
          description: name of the area
          type: string
        polygons:
          description: polygons of GPS coordinates points defining the area
          type: array
          items:
            type: array
            items:
              type: number
  trusters:
    description: public keys of trusters that should be used to process this referendum
    type: array
    items:
      description: public key of the truster
      type: string
      contentEncoding: base64
  websites:
    description: websites providing more information about the referendum
    type: array
    items:
      type: string
      format: uri
```

# Exemple

```yaml
key: referendum_public_key
signature: referendum_signature
published: 2019-09-12T12:33:21+00:00
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
trusters:
- key: truster1_public_key
  trust: 0.9
- key: truster2_public_key
  trust: 0.7
websites:
- https://www.myreferendum.com
- https://www.my-referendum.net
```
