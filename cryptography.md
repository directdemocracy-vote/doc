# Cryptography

directdemocracy heavily relies on cryptography to assess the uniqueness of cards, ensure the anonymity of votes and guarantee the authentication of results.

Participants should create public/private 2048-bit key pairs using the RSA algorithm.
The hash algorithm used for signatures should be SHA-256.

The public keys stored in JSON structures are stripped down version of the standard public key.
The header and footer line are suppressed as well as the new lines.
Considering the following public key:
```
-----BEGIN PUBLIC KEY-----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAkoSFvGywo4sb0crZlmDJ
R7iOSSioDS/ujo4dI0ISYezTVSBnuMvdEtCNfjIXUXy5fMbemrCB8GaragdJQf3w
5xCKYjVSHlU2CEglTz0tgKTfm00/eoBPoW0oEaHRovVkwtaMDECvN8DyWBsA0XqV
GXQsSYa3WA9s0CaaWv9+za1N1Lfv6gKxXMItWcMBcBnPqj2mcl3qgbp635maIkSM
k9/ybH80kv8lxkc/VFsAWsLykcMSZdgNWaxWvNXl6zES8ZkNfOnXHYztbIm25Hjr
ixjan50H4C04HkvvLILFXsNylxOz7vZNYauO6Oh2Jn8IkKzTtXuxaLmh7KuzrLSk
1QIDAQAB
-----END PUBLIC KEY-----
```
The value stored in the JSON structure is:
```
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAkoSFvGywo4sb0crZlmDJR7iOSSioDS/ujo4dI0ISYezTVSBnuMvdEtCNfjIXUXy5fMbemrCB8GaragdJQf3w5xCKYjVSHlU2CEglTz0tgKTfm00/eoBPoW0oEaHRovVkwtaMDECvN8DyWBsA0XqVGXQsSYa3WA9s0CaaWv9+za1N1Lfv6gKxXMItWcMBcBnPqj2mcl3qgbp635maIkSMk9/ybH80kv8lxkc/VFsAWsLykcMSZdgNWaxWvNXl6zES8ZkNfOnXHYztbIm25Hjrixjan50H4C04HkvvLILFXsNylxOz7vZNYauO6Oh2Jn8IkKzTtXuxaLmh7KuzrLSk1QIDAQAB
```

The commands to generate a RSA key pair with 2048 bits are:
```bash
openssl genpkey -algorithm RSA -out id_rsa -pkeyopt rsa_keygen_bits:2048
openssl rsa -pubout -in id_rsa -out id_rsa.pub
```
`id_rsa` is the private key.
`id_rsa.pub` is the public key.
