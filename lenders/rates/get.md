# GET /lenders/rates

Gets estimated financing rates from LeaseQ's marketplace of Lenders.

_Note: These are estimated rates. Actual rates will vary based on actual credit rating of customer and/or business._

**URL** : `/lenders/rates`

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
    "credit_tiers" : [{ 
        "credit_tier": "string | The borrower's credit tier (i.e. A,B,C,D)",

        "terms" : [{ 
            "term_length": "number | The term length in months",
            
            "rates" : [{ 
                "amount_min": "number | The minimum finance amount",
                "amount_max": "number | The maximum finance amount",
                "rate": "number | The estimated average lender financing rate",
                "factor": "number | The estimated average lender financing money factor. This can be used to calculate monthly payment (e.g. monthly payment = money factor × finance amount)"
            }] 
        }] 
    }]
}
```

***Example***

```json
{
    "credit_tiers": [
        {
            "credit_tier": "A",
            "terms": [
                {
                    "term_length": 60,
                    "rates": [
                        {
                            "amount_min": 1,
                            "amount_max": 4999.99,
                            "rate": 0.11718,
                            "factor": 0.0221
                        },
                        {
                            "amount_min": 5000,
                            "amount_max": 9999.99,
                            "rate": 0.11718,
                            "factor": 0.0221
                        }
                    ]
                },
                {
                    "term_length": 48,
                    "rates": [
                        {
                            "amount_min": 1,
                            "amount_max": 4999.99,
                            "rate": 0.1193,
                            "factor": 0.0263
                        },
                        {
                            "amount_min": 5000,
                            "amount_max": 9999.99,
                            "rate": 0.1193,
                            "factor": 0.0263
                        }
                    ]
                },
            ]
        },
        {
            "credit_tier": "B",
            "terms": [
                {
                    "term_length": 60,
                    "rates": [
                        {
                            "amount_min": 1,
                            "amount_max": 4999,
                            "rate": 0.21437,
                            "factor": 0.00893
                        },
                        {
                            "amount_min": 5000,
                            "amount_max": 9999,
                            "rate": 0.21437,
                            "factor": 0.00893
                        }
                    ]
                },
                {
                    "term_length": 48,
                    "rates": [
                        {
                            "amount_min": 1,
                            "amount_max": 4999,
                            "rate": 0.2125,
                            "factor": 0.00885
                        },
                        {
                            "amount_min": 5000,
                            "amount_max": 9999,
                            "rate": 0.2125,
                            "factor": 0.00885
                        }
                    ]
                }
            ]
        }
    ]
}
```

## Error Response

### If not authorized.

**Code** : `401 UNAUTHORIZED`
