# referendum

| field       | data type | comment                                                                           |
| ----------- | --------- | --------------------------------------------------------------------------------- |
| area        | polygon   | should match a well known area published in some online database such as geonames |
| title       | string    |                                                                                   |
| description | string    |                                                                                   |
| question    | string    |                                                                                   |
| answers     | string    | coma separated list of possible answers, e.g., yes, no, abstain                   |
| public key  | key       | not necessarily a citizen public key                                              |
| signature   | signature |                                                                                   |
