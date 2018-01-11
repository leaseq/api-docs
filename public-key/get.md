# GET /public-key

Get the RSA public key for encrypting sensitive fields.

_See [Encryption of Sensitive Data](../encryption.md) for information on encrypting sensitive fields like SSN._

**URL** : `/public-key`

**Method** : `GET`

**Request Headers**

| Name | Value |
|:-----|:------|
|Accept|application/json|

## Success Response

**Code** : `200 OK`

**Response Body**

```json
"string | a base64-encoded RSA public key"
```

***Example***

```json
"LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQklqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FROEFNSUlCQ2dLQ0FRRUEyT2dlWmRtTG9oZjhXWVJhc0JXZAp1blVtWmVPYlJMcW9ucEZ3OW5yVk9QODVmU1ZQUFNNZkx6U2VqNURNRDQwTGU4TjBpcUFKYWxLOG1mbWUreE5xCjR4MnI4QXl0bWlBRlFpOFNxQlZuVVF5MVFtbjhWSnZ3bmZkYlFsb1N0VUVyYzgxUzRRZ1ZzY0NDQW1HcFNFVi8KMXJORFNLMDJZRlFJVGdsU1dDaWptVGJZRE1YWWZKbEtCclFsNlBKYlh6SWRzaklFL3YwMGNIb2xLSWZhaDdlVwpaT0l4NitPWnZPaDhHa0N2UmFjcmRJQ2ZaUkYyZFZnVS84d3RHa1NuN1NERDh2UE1DOVRPU0JiaTFJTW5YYmZDCjVHeGxPVk53RkdBQkRxaDh6aG1yR0R3M1BiUmFpZWQzaUJzRXBUVlV2blE3d0JMaC9xd3lkR3lDK1FSSTYwNTYKalFJREFRQUIKLS0tLS1FTkQgUFVCTElDIEtFWS0tLS0tCg=="
```