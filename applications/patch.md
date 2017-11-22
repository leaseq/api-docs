# PATCH /applications/{application_id}

Update the status of current application that’s been submitted to the LeaseQ Platform.

**URL** : `/applications/{application_id}`

**Method** : `PATCH`

**Request Headers**

| Name | Value |
|:-----|:------|
|Accept|application/json|
|Authorization|LeaseQ Auth Token|

**Request Body**

```json
{
    "status": "string | reqired | The application status - LEAD, APPROVED, TODO",
    "lost_reason": "string | optional | The reason if lost"
}
```

***Example***

```json
{
    "status": "Lost",
    "lost_reason": "Lost To Cash"
}
```

## Success Response

**Code** : `200 OK`

**Response Body**

```json
{
    "status": "string | The application status"
}
```

***Example***

```json
{
    "status": "LOST"
}
```

## Error Response

### If not authorized.

**Code** : `401 UNAUTHORIZED`

### If missing.

**Code** : `404 NOT FOUND`
