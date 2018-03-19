# GET /applications/{application_id}

Get information (status) of current application that’s been submitted to the LeaseQ Platform.

**URL** : `/applications/{application_id}`

**Method** : `GET`

**Request Headers**

| Name | Value |
|:-----|:------|
|Accept|application/json|
|Authorization|[LeaseQ Auth Token](../README.md#authorization-header)|

## Success Response

**Code** : `200 OK`

**Response Body**

```json
{
    "app_id": "guid | The id of the new application",
    "remote_id": "string | An optional identifier that can be set to correlate LeaseQ applications with entities in other systems. This field is searchable in the LeaseQ dashboard",
    "status": "string | The application status - e.g. New, Lead, AppIn, AppSubmitted, Decline, Approved, etc.", 
    "lender" : "string | The lender name",
    "total_amount" : "number | The total amount",
    "updated_date" : "string | The date/time when the application was last updated.",
}
```

***Example***

```json
{
    "app_id": "GUID",
    "remote_id": "eb9838f3-8d3f-fe24-eff0-d180d3fd513a",
    "status": "Approved",
    "lender": "ACME Lending",
    "total_amount" : 20000.0,
    "updated_date": "2018-03-19T15:43:53.828Z"
}
```

## Error Response

### If not authorized.

**Code** : `401 UNAUTHORIZED`

### If missing.

**Code** : `404 NOT FOUND`
