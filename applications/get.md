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
    "status": "string | The application status - LEAD, APPROVED, TODO", 
    "term" : "string | The term length",
    "lender" : { 
        "name" : "string | The lender name" 
    },
    "signed_date" : "TODO",
    "approved_date" : "TODO",
    "funded_date" : "TODO",
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
    "term" : "60",
    "lender" : { 
        "name" : "ACME Lending" 
    },
    "signed_date" : "",
    "approved_date" : "",
    "funded_date" : "",
    "products " : [  
    { 
        "product_id " : "SBIR_Pr_Code ",
        "quantity" : 3,
        "discounted_price ": 4000 
    },
	{
        "product_id" : "SBIR_Pr_Code",
        "quantity " : 2,
        "discounted_price ": 3000 }
    ], 
}
```

## Error Response

### If not authorized.

**Code** : `401 UNAUTHORIZED`

### If missing.

**Code** : `404 NOT FOUND`
