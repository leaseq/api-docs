# GET /applications/{application_id}/quotes

Gets pre-qualified financing quotes from LeaseQ's marketplace of Lenders.

**URL** : `/applications/{application_id}/quotes`

**Method** : `GET`

**Request Headers**

| Name | Value |
|:-----|:------|
|Accept|application/json|
|Authorization|[LeaseQ Auth Token](../../README.md#authorization-header)|

## Success Response

**Code** : `200 OK`

**Response Body**

```json
{
    "quotes" : [{ 
        "quote_id": "guid | The quote id",
        "lender_name": "string | The lender name",
        "finance_type": "string | The type of financing (e.g. '$1 Buyout')",
        "details": "string | Additional details",

        "options":[{
            "option_id": "guid | The option id",
            "term_length": "number | The term length in months",
            "monthly_payment": "number | The monthly payment"
        }]
    }]
}
```

***Example***

```json
{
    "quotes" : [{ 
        "quote_id": "00000000-0000-0000-0000-000000000000",
        "lender_name": "ACME Capital",
        "finance_type": "$1 Buyout",
        "details": "First and last payment are due upfront. Documentation fee $200. Rates do not include sales, rental or use taxes. Fair market value purchase available at end of lease.",
        
        "options":[{
            "option_id": "00000000-0000-0000-0000-000000000000",
            "term_length": 60,
            "monthly_payment": 537.00,
        },{
            "option_id": "00000000-0000-0000-0000-000000000000",
            "term_length": 48,
            "monthly_payment": 646.00,
        },{
            "option_id": "00000000-0000-0000-0000-000000000000",
            "term_length": 36,
            "monthly_payment": 829.00,
        },{
            "option_id": "00000000-0000-0000-0000-000000000000",
            "term_length": 24,
            "monthly_payment": 1185.00
        }]
    }]
}
```

## Error Response

### If not authorized.

**Code** : `401 UNAUTHORIZED`

### If application is not found.

**Code** : `404 NOT FOUND`
