# referendum

```yaml
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
key: referendum_public_key
signature: referendum_signature
```
