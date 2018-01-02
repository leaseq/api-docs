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
                "rate": "number | The estimated average lender financing rate"
            }] 
        }] 
    }]
}
```

***Example***

```json
{
    "credit_tiers" : [{ 
        "credit_tier": "A",

        "terms" : [{ 
            "term_length": 12,

            "rates" : [{ 
                "amount_min": 1,
                "amount_max": 4999,
                "rate": 0.0805
            },{
                "amount_min": 5000,
                "amount_max": 9999,
                "rate": 0.0814
            },{
                "amount_min": 10000,
                "amount_max": 49999,
                "rate": 0.0818
            },{
                "amount_min": 50000,
                "amount_max": 249999,
                "rate": 0.0822
            }]
        },{ 
            "term_length": 24,

            "rates" : [{ 
                "amount_min": 1,
                "amount_max": 4999,
                "rate": 0.0910
            },{
                "amount_min": 5000,
                "amount_max": 9999,
                "rate": 0.0914
            },{
                "amount_min": 10000,
                "amount_max": 49999,
                "rate": 0.0918
            },{
                "amount_min": 50000,
                "amount_max": 249999,
                "rate": 0.0922
            }]
        }]
    },{
        "credit_tier": "B",

        "terms" : [{ 
            "term_length": 12,

            "rates" : [{ 
                "amount_min": 1,
                "amount_max": 4999,
                "rate": 0.0811
            },{
                "amount_min": 5000,
                "amount_max": 9999,
                "rate": 0.0815
            },{
                "amount_min": 10000,
                "amount_max": 49999,
                "rate": 0.0819
            },{
                "amount_min": 50000,
                "amount_max": 249999,
                "rate": 0.0823
            }]
        },{ 
            "term_length": 24,

            "rates" : [{ 
                "amount_min": 1,
                "amount_max": 4999,
                "rate": 0.0911
            },{
                "amount_min": 5000,
                "amount_max": 9999,
                "rate": 0.0915
            },{
                "amount_min": 10000,
                "amount_max": 49999,
                "rate": 0.0919
            },{
                "amount_min": 50000,
                "amount_max": 249999,
                "rate": 0.0923
            }]
        }]
    }]
}
```

## Error Response

### If not authorized.

**Code** : `401 UNAUTHORIZED`