# Publication

A publication is a JSON file that is published at one or several places on the Internet, including at [publishers](publisher.md).
It includes at least the following fields:
- `schema`: the URL of the JSON schema
- `key`: the public key of the author
- `signature`: the signature of the author
- `published`: the publication date
- `expires`: date after which the publication is obsolete

The JSON file is originally created with an empty signature field.
It is then [signed](cryptography.md) and the signature value is inserted into the signature field.
