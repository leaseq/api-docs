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
                            "amount_max": 4999,
                            "rate": 0.11718,
                            "factor": 0.00488
                        },
                        {
                            "amount_min": 5000,
                            "amount_max": 9999,
                            "rate": 0.11718,
                            "factor": 0.00488
                        },
                        {
                            "amount_min": 10000,
                            "amount_max": 19999,
                            "rate": 0.0855,
                            "factor": 0.00356
                        },
                        {
                            "amount_min": 20000,
                            "amount_max": 29999,
                            "rate": 0.0855,
                            "factor": 0.00356
                        },
                        {
                            "amount_min": 40000,
                            "amount_max": 49999,
                            "rate": 0.0855,
                            "factor": 0.00356
                        }
                    ]
                },
                {
                    "term_length": 48,
                    "rates": [
                        {
                            "amount_min": 1,
                            "amount_max": 4999,
                            "rate": 0.1193,
                            "factor": 0.00497
                        },
                        {
                            "amount_min": 5000,
                            "amount_max": 9999,
                            "rate": 0.1193,
                            "factor": 0.00497
                        },
                        {
                            "amount_min": 10000,
                            "amount_max": 19999,
                            "rate": 0.0859,
                            "factor": 0.00358
                        },
                        {
                            "amount_min": 20000,
                            "amount_max": 29999,
                            "rate": 0.0859,
                            "factor": 0.00358
                        },
                        {
                            "amount_min": 40000,
                            "amount_max": 49999,
                            "rate": 0.0859,
                            "factor": 0.00358
                        }
                    ]
                },
                {
                    "term_length": 36,
                    "rates": [
                        {
                            "amount_min": 1,
                            "amount_max": 4999,
                            "rate": 0.1489,
                            "factor": 0.0062
                        },
                        {
                            "amount_min": 5000,
                            "amount_max": 9999,
                            "rate": 0.1489,
                            "factor": 0.0062
                        },
                        {
                            "amount_min": 10000,
                            "amount_max": 19999,
                            "rate": 0.0903,
                            "factor": 0.00376
                        },
                        {
                            "amount_min": 20000,
                            "amount_max": 29999,
                            "rate": 0.0903,
                            "factor": 0.00376
                        },
                        {
                            "amount_min": 40000,
                            "amount_max": 49999,
                            "rate": 0.0903,
                            "factor": 0.00376
                        }
                    ]
                },
                {
                    "term_length": 24,
                    "rates": [
                        {
                            "amount_min": 1,
                            "amount_max": 4999,
                            "rate": 0.1635,
                            "factor": 0.00681
                        },
                        {
                            "amount_min": 5000,
                            "amount_max": 9999,
                            "rate": 0.1635,
                            "factor": 0.00681
                        },
                        {
                            "amount_min": 10000,
                            "amount_max": 19999,
                            "rate": 0.096,
                            "factor": 0.004
                        },
                        {
                            "amount_min": 20000,
                            "amount_max": 29999,
                            "rate": 0.096,
                            "factor": 0.004
                        },
                        {
                            "amount_min": 40000,
                            "amount_max": 49999,
                            "rate": 0.096,
                            "factor": 0.004
                        }
                    ]
                },
                {
                    "term_length": 12,
                    "rates": [
                        {
                            "amount_min": 1,
                            "amount_max": 4999,
                            "rate": 0.1818,
                            "factor": 0.00757
                        },
                        {
                            "amount_min": 5000,
                            "amount_max": 9999,
                            "rate": 0.1818,
                            "factor": 0.00757
                        },
                        {
                            "amount_min": 10000,
                            "amount_max": 19999,
                            "rate": 0.1318,
                            "factor": 0.00549
                        },
                        {
                            "amount_min": 20000,
                            "amount_max": 29999,
                            "rate": 0.1318,
                            "factor": 0.00549
                        },
                        {
                            "amount_min": 40000,
                            "amount_max": 49999,
                            "rate": 0.1318,
                            "factor": 0.00549
                        }
                    ]
                }
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
                        },
                        {
                            "amount_min": 10000,
                            "amount_max": 19999,
                            "rate": 0.0866,
                            "factor": 0.00361
                        },
                        {
                            "amount_min": 20000,
                            "amount_max": 29999,
                            "rate": 0.0866,
                            "factor": 0.00361
                        },
                        {
                            "amount_min": 40000,
                            "amount_max": 49999,
                            "rate": 0.0866,
                            "factor": 0.00361
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
                        },
                        {
                            "amount_min": 10000,
                            "amount_max": 19999,
                            "rate": 0.0923,
                            "factor": 0.00385
                        },
                        {
                            "amount_min": 20000,
                            "amount_max": 29999,
                            "rate": 0.0923,
                            "factor": 0.00385
                        },
                        {
                            "amount_min": 40000,
                            "amount_max": 49999,
                            "rate": 0.0923,
                            "factor": 0.00385
                        }
                    ]
                },
                {
                    "term_length": 36,
                    "rates": [
                        {
                            "amount_min": 1,
                            "amount_max": 4999,
                            "rate": 0.25916,
                            "factor": 0.0108
                        },
                        {
                            "amount_min": 5000,
                            "amount_max": 9999,
                            "rate": 0.25916,
                            "factor": 0.0108
                        },
                        {
                            "amount_min": 10000,
                            "amount_max": 19999,
                            "rate": 0.0964,
                            "factor": 0.00402
                        },
                        {
                            "amount_min": 20000,
                            "amount_max": 29999,
                            "rate": 0.0964,
                            "factor": 0.00402
                        },
                        {
                            "amount_min": 40000,
                            "amount_max": 49999,
                            "rate": 0.0964,
                            "factor": 0.00402
                        }
                    ]
                },
                {
                    "term_length": 24,
                    "rates": [
                        {
                            "amount_min": 1,
                            "amount_max": 4999,
                            "rate": 0.26935,
                            "factor": 0.01122
                        },
                        {
                            "amount_min": 5000,
                            "amount_max": 9999,
                            "rate": 0.26935,
                            "factor": 0.01122
                        },
                        {
                            "amount_min": 10000,
                            "amount_max": 19999,
                            "rate": 0.0974,
                            "factor": 0.00406
                        },
                        {
                            "amount_min": 20000,
                            "amount_max": 29999,
                            "rate": 0.0974,
                            "factor": 0.00406
                        },
                        {
                            "amount_min": 40000,
                            "amount_max": 49999,
                            "rate": 0.0974,
                            "factor": 0.00406
                        }
                    ]
                },
                {
                    "term_length": 12,
                    "rates": [
                        {
                            "amount_min": 1,
                            "amount_max": 4999,
                            "rate": 0.28991,
                            "factor": 0.01208
                        },
                        {
                            "amount_min": 5000,
                            "amount_max": 9999,
                            "rate": 0.28991,
                            "factor": 0.01208
                        },
                        {
                            "amount_min": 10000,
                            "amount_max": 19999,
                            "rate": 0.142,
                            "factor": 0.00592
                        },
                        {
                            "amount_min": 20000,
                            "amount_max": 29999,
                            "rate": 0.142,
                            "factor": 0.00592
                        },
                        {
                            "amount_min": 40000,
                            "amount_max": 49999,
                            "rate": 0.142,
                            "factor": 0.00592
                        }
                    ]
                }
            ]
        },
    ]
}
```

## Error Response

### If not authorized.

**Code** : `401 UNAUTHORIZED`
