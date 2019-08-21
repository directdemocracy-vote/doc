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
    -  etc.
  - etc.
 - type: country
   name: Switzerland
trusters:
- key: truster1_public_key
  trust: truster1_trust_level
- key: truster2_public_key
  trust: truster2_trust_level
key: my_public_key
signature: my_signature
```
