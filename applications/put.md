# PUT /applications/{application_id}

Update an existing application in the LeaseQ Platform.

**URL** : `/applications/{application_id}`

**Method** : `PUT`

**Request Headers**

| Name | Value |
|:-----|:------|
|Accept|application/json|
|Authorization|LeaseQ Auth Token|

**Request Body**

```json
{
    "type": "string | required | The application type - business, consumer, corporate, nonprofit, municipal",
    "total_amount": "number | optional | The total amount",

    "products": [{
        "product_code": "string | required | The product code",
        "name": "string | required | The product name",
        "description": "string | required | The product description",
        "quantity": "number | optional | The product quantity",
        "price": "number | required | The product price",
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
        "zip": "string | required | The zip/postal of the company headquarters"
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
        "percentage_owned": "string | required | The percentage owned",
    }]
}
```

***Example***

```json
{
    "type": "business",
    "total_amount":20000,

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
        "zip": "01802"
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
        "percentage_owned": "100"
    }]
}
```

## Success Response

**Code** : `201 OK`

**Response Body**

```json
{
    "app_id": "guid | The id of the application",
    "status": "string | The status of the new application - Funded, Lost, PO Issued, Prefunding Released, Contract In, Contract Out, Approved, App Submitted, Decline, App Widget Lead, New", ",
}
```

***Example***

```json
{
    "app_id": "00000000-0000-0000-0000-000000000000",
    "status": "LEAD",
}
```

## Error Response

### If not authorized.

**Code** : `401 UNAUTHORIZED`
