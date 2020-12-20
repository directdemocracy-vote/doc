# Area

## Description

An area is a [publication](publication.md) representing a geographic zones defined by a set of polygons and used to delimit the boundaries of a referendum.
Polygons are expressed in the GeoJSON MultiPolygon format.
The name should match the area field of the referendum.
It is usually published by the trustee of the referendum.

## Format

https://directdemocracy.vote/json-schema/0.0.1/area.schema.json

## Example

```yaml
schema: https://directdemocracy.vote/json-schema/0.0.1/area.schema.json
key: public_key
signature: signature_for_area
published: 1574679658399
expires: 1890298858399
name: |
  city=Mâcon
  county=Saône-et-Loire
  state=Bourgogne-Franche-Comté
  country=France
  union=European Union
polygons: [[[[ 12.123, 123.121 ], [12.112, 134.113], [12.321. 107.122]]]]
```
