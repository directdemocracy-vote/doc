# referendum

```yaml
title: my referendum
description: my description
question: do you agree?
answers:
- yes
- no
- abstain
deadline: date
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
- truster1_public_key
  truster1
- truster2_public_key
key: my_public_key
signature: my_signature
```
