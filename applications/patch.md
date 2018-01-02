# PATCH /applications/{application_id}

Update the status of current application that’s been submitted to the LeaseQ Platform.

**URL** : `/applications/{application_id}`

**Method** : `PATCH`

**Request Headers**

| Name | Value |
|:-----|:------|
|Accept|application/json|
|Authorization|[LeaseQ Auth Token](../README.md#authorization-header)|

**Request Body**

```json
{
    "status": "string | required | The application status - Funded, Lost, PO Issued, Prefunding Released, Contract In, Contract Out, Approved, App Submitted, Decline, App In, Leads",
    "lost_reason": "string | optional | The reason if status is Lost"
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
