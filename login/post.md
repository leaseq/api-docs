# POST /login

Login API requires email address, password and dealer id of an account to authenticate the user. As a response you will receive a “auth token along with “auth scheme” and “expires” in json.  This auth token along with auth scheme will be required for every subsequent API calls.  All the calls are authorized based on the privileges of account role. The LeaseQ platform supports two different roles “admin” and “salesperson”.  Auth token is valid only for time specified in “expire” and will get renewed for every HTTP call made to API endpoint.

**URL** : `/login`

**Method** : `POST`

**Request Headers**

| Name | Value |
|:-----|:------|
|Accept|application/json|

**Request Body**

```json
{ 
    "email": "string | required | your email address", 
    "password": "string | required | your password",   
    "tenant_id" : "string | required | your tennant or dealer id",
} 
```

***Example***

```json
{ 
    "email": "user@example.com", 
    "password": "StrongPassword",   
    "tenant_id" : "<tennant or dealer id>",
} 
```

## Success Response

**Code** : `200 OK`

**Response Body**

```json
{	  
    "auth_token": "string | The authentication token",
    "auth_scheme": "string | The authentication scheme",
    "expires": "date/time | The expiration date/time of the token",
}
```

***Example***
```json
{	  
    "auth_token": "<token>",
    "auth_scheme": "LeaseQ",
    "expires": "Mon, 01 Jan 2000 00:00:00 GMT",
}
```

## Error Response

### If 'username' and 'password' combination is wrong.

**Code** : `401 UNAUTHORIZED`

**Response Body** :

```json
{
    "non_field_errors": [
        "Unable to login with provided credentials."
    ]
}
```