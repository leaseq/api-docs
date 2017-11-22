# GET /applications/{application_id}

Get information (status) of current application that’s been submitted to the LeaseQ Platform.

**URL** : `/applications/{application_id}`

**Method** : `GET`

**Request Headers**

| Name | Value |
|:-----|:------|
|Accept|application/json|
|Authorization|LeaseQ Auth Token|

## Success Response

**Code** : `200 OK`

**Response Body**

```json
{
    "app_id": "guid | The id of the new application",
    "status": "string | required | The application status - Funded, Lost, PO Issued, Prefunding Released, Contract In, Contract Out, Approved, App Submitted, Decline, App Widget Lead, New", 
    "term" : "string | The term length",
    "lender" : { 
        "name" : "string | The lender name" 
    },
    "signed_date" : "1/1/2001",
    "approved_date" : "1/1/2001",
    "funded_date" : "1/1/2001",
    "products " : [{ 
        "product_code": "string | required | The product code",
        "quantity": "number | optional | The product quantity",
        "discounted_price": "number | optional | The discounted price"
    }], 
}
```

***Example***

```json
{
    "app_id": "GUID",
    "status": "APPROVED",
    "term": "60",
    "lender": {
        "name": "ACME Lending"
    },
    "signed_date": "",
    "approved_date": "",
    "funded_date": "",
    "products ": [{
        "product_id ": "SBIR_Pr_Code ",
        "quantity": 3,
        "discounted_price ": 4000
    }, {
        "product_id": "SBIR_Pr_Code",
        "quantity ": 2,
        "discounted_price ": 3000
    }],
}
```

## Error Response

### If not authorized.

**Code** : `401 UNAUTHORIZED`

### If missing.

**Code** : `404 NOT FOUND`
