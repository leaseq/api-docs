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
    "type": "string | The application type - business, consumer, corporate, nonprofit, municipal",
    "is_full_application" : "boolean | A flag which indicates this application should be validated as a complete application that requires no additional information from guarantors",
    "total_amount": "number | The total amount to be financed",
    "remote_id": "string | An identifier that can be set to correlate LeaseQ applications with entities in other systems. This field is searchable in the LeaseQ dashboard",

    "products": [{
        "type": "string | The product type - See 'Product Types' link",
        "condition": "string | The condition of the equipment - 'new' | 'used'",
        "product_code": "string | The product code",
        "name": "string | The product name",
        "description": "string | The product description",
        "quantity": "number | The product quantity",
        "price": "number | The product price"
    }],

    "billing": [{
        "charge": "string | The charge / line item",
        "description": "string | The description of the charge",
        "price": "number | The price"
    }],

    "company": {
        "name": "string | The name of the company",
        "dba": "string | The name under which the company does business",
        "phone": "string | The phone number for the company headquarters",
        "address": "string | The company headquarters street address",
        "city": "string | The city where the company headquarters is located ",
        "state": "string | The state/prov where the company headquarters is located",
        "zip": "string | The zip/postal of the company headquarters",
        "ein": "string | The Employer Identification Number",
        "years_in_business" : "number | The number of years in business",
        "structure": "string | The company ownership structure - See 'Company Structures' link"
    },

    "guarantors": [{
        "first_name": "string | The guarantor's first name",
        "last_name": "string | The guarantor's last name",
        "email": "string | The guarantor's email address",
        "phone": "string | The guarantor's phone number",
        "address": "string | The guarantor's street address",
        "city": "string | The guarantor's city",
        "state": "string | The guarantor's state/prov",
        "zip": "string | The guarantor's zip/postal",
        "ssn": "encrypted string | The guarantor's Social Security Number - See 'Encryption of Sensitive Data' Link",
        "percentage_owned": "string | The percentage owned"
    }],

    "owns_install_location": "boolean | Indicates whether the customer owns the property where the equipment is being installed" 
}
```

***Links***

* [Product Types](./README.md#product-types)
* [Company Structures](./README.md#company-structures)
* [Encryption of Sensitive Data](../encryption.md)

**Required Fields**

| Field                       	    | Partial Credit Application 	| Full Credit Application (`is_full_application` = true) |
|----------------------------------	|:-----------:	|:--------:	|
| `type`                        	|      ●      	|     ●    	|
| `is_full_application`            	|           	|     ●    	|
| `total_amount`                	|             	|     ●    	|
| `remote_id`                   	|             	|          	|
| `products[]`                    	|             	|          	|
| `products[].type`                	|      ●      	|     ●    	|
| `products[].condition`           	|      ●      	|     ●    	|
| `products[].product_code`       	|      ●      	|     ●    	|
| `products[].name`                 |      ●      	|     ●    	|
| `products[].description`        	|      ●      	|     ●    	|
| `products[].quantity`           	|             	|          	|
| `products[].price`              	|      ●      	|     ●    	|
| `billing[]`                     	|             	|          	|
| `billing[].charge`              	|      ●      	|     ●    	|
| `billing[].description`         	|             	|          	|
| `billing[].price`               	|      ●      	|     ●    	|
| `company`                     	|             	|     ●    	|
| `company.name`                	|             	|     ●    	|
| `company.dba`                 	|             	|          	|
| `company.phone`               	|             	|     ●    	|
| `company.address`             	|             	|     ●    	|
| `company.city`                	|             	|     ●    	|
| `company.state`               	|             	|     ●    	|
| `company.zip`                 	|             	|     ●    	|
| `company.ein`                 	|             	|          	|
| `company.years_in_business`   	|             	|     ●    	|
| `company.structure`              	|             	|     ●    	|
| `guarantors[]`                  	|      ●      	|          	|
| `guarantors[].first_name`       	|             	|     ●    	|
| `guarantors[].last_name`        	|             	|     ●    	|
| `guarantors[].email`            	|      ●      	|     ●    	|
| `guarantors[].phone`            	|             	|     ●    	|
| `guarantors[].address`          	|             	|     ●    	|
| `guarantors[].city`             	|             	|     ●    	|
| `guarantors[].state`            	|             	|     ●    	|
| `guarantors[].zip`              	|             	|     ●    	|
| `guarantors[].ssn`              	|             	|     ●    	|
| `guarantors[].percentage_owned` 	|             	|     ●    	|
| `owns_install_location`       	|             	|          	|

***Example - Partial Credit Application***

Submitting a "partial" credit application starts the application process. The guarantors you list will receive an email containing a link for them to complete the application. This is the preferred submission method for vendors who do not know or do not want to handle the guarantor's sensitive information.

```json
{
    "type": "business",

    "company": {
        "name": "ABC Corp"
    },

    "guarantors": [{
        "first_name": "John",
        "last_name": "Doe",
        "email": "john.doe@example.com"
    }]
}
```

***Example - Full Credit Application***

A "full" credit application contains all information necessary to receive instant financing quotes. The guarantors you list will not be required to provide any additional information when you use this submission method.

```json
{
    "type": "business",
    "is_full_application": true,
    "total_amount": 20733.89,
    "remote_id": "eb9832f3-8d3f-fe24-eff0-d180d3fd513a",

    "products": [{
        "type": "restaurant",
        "product_code": "ICE10000",
        "name": "Ice Maker",
        "description": "Capacities up to 2900 pounds per day",
        "condition": "new",
        "quantity": 2,
        "price": 2830
    }, {
        "type": "restaurant",
        "product_code": "CBG20388",
        "name": "Gas Charbroiler",
        "description": "24-inch gas broiler",
        "condition": "new",
        "quantity": 3,
        "price": 777
    }, {
        "type": "restaurant",
        "product_code": "RF38271",
        "name": "Display Freezer",
        "description": "Two-section display freezer",
        "condition": "new",
        "quantity": 2,
        "price": 4992.3
    }],

    "billing": [{
        "charge": "Tax",
        "description": "7 percent tax",
        "price": 1258.29
    }, {
        "charge": "Delivery charge",
        "description": "Delivery charge",
        "price": 1500
    }],

    "company": {
        "name": "ABC Restaurant",
        "dba": "ABC",
        "phone": "7815555555",
        "address": "17 North Ave",
        "city": "Boston",
        "state": "MA",
        "zip": "01802",
        "ein": "00-0000000",
        "years_in_business": 5,
        "structure": "llc"
    },

    "guarantors": [{
        "first_name": "John",
        "last_name": "Doe",
        "email": "john.doe@example.com",
        "phone": "7815555555",
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
