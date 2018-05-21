# POST /applications

Submit a new credit application to LeaseQ Platform.

**URL** : `/applications`

**Method** : `POST`

**Request Headers**

| Name | Value |
|:-----|:------|
|Accept|application/json|
|Authorization|[LeaseQ Auth Token](../README.md#authorization-header)|

**Request Body**

```json
{
    "type": "string | required | The application type - business, consumer, corporate, nonprofit, municipal",
    "total_amount": "number | required | The total amount",
    "remote_id": "string | optional | An optional identifier that can be set to correlate LeaseQ applications with entities in other systems. This field is searchable in the LeaseQ dashboard",

    "products": [{
        "product_code": "string | required | The product code",
        "name": "string | required | The product name",
        "description": "string | required | The product description",
        "quantity": "number | optional | The product quantity",
        "price": "number | required | The product price"
    }],

    "billing": [{
        "charge": "string | required | The charge / line item",
        "description": "string | optional | The description of the charge",
        "price": "number | required | The price"
    }],

    "company": {
        "name": "string | required | The name of the company",
        "dba": "string | optional | The name under which the company does business",
        "phone": "string | required | The phone number for the company headquarters",
        "address": "string | required | The company headquarters street address",
        "city": "string | required | The city where the company headquarters is located ",
        "state": "string | required | The state/prov where the company headquarters is located",
        "zip": "string | required | The zip/postal of the company headquarters",
        "ein": "string | optional | The Employer Identification Number",
        "years_in_business" : "number | required | The number of years in business",
        "bus_type" : "string | required | Business structure of company - c_corp, s_corp, llc, partnership, sole_prop"        
    },

    "guarantors": [{
        "first_name": "string | required | The guarantor's first name",
        "last_name": "string | required | The guarantor's last name",
        "email": "string | required | The guarantor's email address",
        "phone": "string | required | The guarantor's phone number",
        "address": "string | required | The guarantor's street address",
        "city": "string | required | The guarantor's city",
        "state": "string | required | The guarantor's state/prov",
        "zip": "string | required | The guarantor's zip/postal",
        "ssn": "encrypted string | required | The guarantor's Social Security Number",
        "percentage_owned": "string | required | The percentage owned"
    }],

    "owns_install_location": "boolean | optional | Indicates whether the customer owns the property where the equipment is being installed",
    "is_partial_application": "boolean | optional | Indicates whether values for all required fields are included in the request" 
}
```

_See [Encryption of Sensitive Data](../encryption.md) for information on encrypting sensitive fields like SSN._

***Example***

```json
{
    "type": "business",
    "total_amount":20000,
    "remote_id":"eb9838f3-8d3f-fe24-eff0-d180d3fd513a",

    "products": [{
        "product_code": "SBIR_Pr_Code",
        "name": "Pepper",
        "description": "Pepper",
        "quantity": 3,
        "price": 4000
    }, {
        "product_code": "SBIR_Pr_Code",
        "name": "Service Plan",
        "description": "Service Plan",
        "quantity": 1,
        "price": 3000
    }],

    "billing": [{
        "charge": "Tax",
        "description": "20 percent tax",
        "price": 250
    }, {
        "charge": "Delivery charge",
        "description": "Delivery charge",
        "price": 100
    }],

    "company": {
        "name": "ABC Corp",
        "dba": "ABC Corp [ optional ]",
        "phone": "7815554433",
        "address": "17 North Ave",
        "city": "Boston",
        "state": "MA",
        "zip": "01802",
        "ein": "00-0000000",
        "years_in_business": 5,
        "bus_type": "c_corp"
    },

    "guarantors": [{
        "first_name": "Paul",
        "last_name": "Testcase",
        "email": "abc@xyz.com",
        "phone": "7815554433",
        "address": "16 Summer St",
        "city": "Boston",
        "state": "MA",
        "zip": "01801",
        "ssn": "hd17v6cWi2ltvwcLi6IDj4rhpkV+fafQOWg8yY756FwB46+POrecRj1dUg+xUcxW7lHtp0WKppB810+Ut++9uWNr6YJvzzemThrKykVw71qfq5ParS2p1YRCwGgfqJNb92V5KasrysMp+gM2kq6QdiSUWN9WhUP/6dkOnR+1CTCe68sS7zLI0JG394X196YN/ERasM5QhNSihQoOlsjw166wZMegviEb2EEm2zKp8A7jchL0ahJFsVO4aXmREIbCuE4jXY6OazWv7aF1BB5jvE7Hdw9SgXPMb/9+HTDOnLkIPqxEuxjZPR6bv6hImFBdeLa7J4xsPMJtghhla3GdndT7Okgn1/Qoq5Wjg1RzvFVp2rsYIMx9YVP74N69ga8f8e1PNd6T4V6coQRAP4U9IGb23BDAINxVbL5mae/LGDSsA6tdaT2pwGmJ90gyioutUSCNPR202zAKYY9280BKphp+GhERsSRKP+yBWCgc5EEJOKSqO/BcNbO3ckmfaNPOSHBnenjfaPogY0KM7jwVZIY5w+6itcOUrMpFLycxZLlqUWo6MOvn/CTsKWkm75uXv0dk/BPDgV1pj4ErMe1ifZyAN0SGF3n/9gSvqqI9IRRhELs5AMM/2AT+O8EDmRxvgO1XIwOu/gzeJ9pyQ1pkF06dlCpmlvTD6s6QZVNTa6s=",
        "percentage_owned": "100"
    }]
}
```

## Success Response

**Code** : `201 CREATED`

**Response Body**

```json
{
    "app_id": "guid | The id of the new application",
    "status": "string | The status of the new application - Funded, Lost, PO Issued, Prefunding Released, Contract In, Contract Out, Approved, App Submitted, Decline, App Widget Lead, New"
}
```

***Example***

```json
{
    "app_id": "00000000-0000-0000-0000-000000000000",
    "status": "New"
}
```

## Error Response

### If not authorized.

**Code** : `401 UNAUTHORIZED`
