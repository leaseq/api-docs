# POST /applications/{application_id}/sign

Electronically signs an application. Specifies which quote and term was selected by the customer and provides consent to perform a hard credit pull.

The quotes for an application can be retrieved from the [quotes API](quotes/get.md).

**URL** : `/applications/{application_id}/sign`

**Method** : `POST`

**Request Headers**

| Name | Value |
|:-----|:------|
|Accept|application/json|
|Authorization|[LeaseQ Auth Token](../README.md#authorization-header)|

**Request Body**

```json
{
    "selected_quote": "guid | required | The id of the selected quote",
    "selected_term": "number | required | The desired term length from the selected quote",
    
    "name": "string | required | The name of the signer",
    "title": "string | required | The title of the signer (e.g. Owner, Principal, CFO, ...)",
    "consent": "string | required | What the signer is consenting to. For example, 'Agreement to perform hard credit pull'"
}
```

***Example***

```json
{
    "selected_quote": "00000000-0000-0000-0000-000000000000",
    "selected_term": 48,
    "name": "John Smith",
    "title": "Owner",
    "consent": "Agreement to perform hard credit pull"
}
```

## Success Response

**Code** : `200 OK`

**Response Body**

```json
{
    "signature":"string | The signature hash",
    "date":"string | The date/time of the signing"
}
```

***Example***

```json
{
    "signature":"o08oAGRZzup8RX7QX4eZRjmSmntgxqE3ROyiQaNCkqk=",
    "date":"2018-01-09T17:07:52.216-06:00"
}
```

## Error Response

### If selected quote or term is not valid.

**Code** : `400 BAD REQUEST`

### If not authorized.

**Code** : `401 UNAUTHORIZED`
