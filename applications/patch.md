# PATCH /applications/{application_id}

Update a portion of an application that’s been submitted to the LeaseQ Platform.

**URL** : `/applications/{application_id}`

**Method** : `PATCH`

**Request Headers**

| Name | Value |
|:-----|:------|
|Accept|application/json|
|Content-Type|application/merge-patch+json|
|Authorization|[LeaseQ Auth Token](../README.md#authorization-header)|

**Request Body**

```json
{
    "status": "string | optional | The application status - Funded, Lost, PO Issued, Prefunding Released, Contract In, Contract Out, Approved, App Submitted, Decline, App In, Leads",
    "lost_reason": "string | optional | The reason if status is Lost",

    "total_amount": "number | optional | The total amount",
}
```

***Example: Update Application Status***

Update the credit application status to indicate the deal was lost and the customer decided to pay with cash.

```json
{
    "status": "Lost",
    "lost_reason": "Lost To Cash"
}
```

***Example: Update Application Total Amount***

Update the credit application so the total amount to be financed  is $100,000.

```json
{
    "total_amount": 100000
}
```

## Success Response

**Code** : `204 NO CONTENT`

## Error Response

### If not authorized.

**Code** : `401 UNAUTHORIZED`

### If application is not found.

**Code** : `404 NOT FOUND`

### If request is invalid.

**Code** : `400 BAD REQUEST`

