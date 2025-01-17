
# Customer Shipments
Customer Shipments are orders submitted to Toolbox Genomics wherein one or more DNA Collection Kits are requested to be shipped directly to a `Customer`. This document explains how to create, retrieve, and cancel customer shipments.

<br>

## Create a Customer Shipment

### POST `/api/v1/customer-shipments/`

| Attribute Name | Data Type | Description
|:---|:---|:---
| customer | integer| The intended recipient of the shipment.  This `id` can be obtained from the Toolbox Genomics API after Customer creation.
| recipient_address | Address | The destination of the shipment.
| recipient_phone | string |
| recipient_name | string |
| sku | string | The SKU of the DNA Collection Kit for shipment.
| quantity | integer | The quantity of the item for shipment.
| notes | string | Delivery notes.
| is_replacement | bool | Indicates whether or not the requested shipment is intended as a replacement kit for the Customer.
 

#### Example Request

```
POST partners.toolboxgenomics.com/api/v1/customer-shipments/
Content-Type: application/json

Payload:
  {
    "customer": 319,
    "recipient_address": {
      "line_1": "2950 Buskirk Avenue",
      "line_2": "Suite 300",
      "city": "Walnut Creek",
      "state": "CA",
      "postal_code": "94597",
      "country: "US"
    },
    "recipient_phone": "(415)722-4393",
    "recipient_name": "Jon Snow",
    "sku": "PT-Kit-1",
    "quantity": 1,
    "is_replacement": false
  }

```

#### Example Response

```
HTTP/1.0 201 OK 
Content-Type: application/json

{
  "id": 70,
  "created_at": "2017-11-24 10:00:00",
  "customer": 319,
  "recipient_address": {
    "line_1": "2950 Buskirk Avenue",
    "line_2": "Suite 300",
    "city": "Walnut Creek",
    "state": "CA",
    "postal_code": "94597",
    "country: "US"
  },
  "recipient_phone": "(415)722-4393",
  "recipient_name": "Jon Snow",
  "sku": "PT-Kit-1",
  "quantity": 1,
  "is_replacement": false
}

```

<br />

## Get a Customer Shipment
### GET `/api/v1/customer-shipment/{customer-shipment-id}`

Retrieve the details of a Customer Shipment by id.

| Attribute Name | Data Type | Description
|:---|:---|:---
| id | integer| System generated `id` of Toolbox Genomics API after Shipment creation.
| created_at | date | The datetime Shipment is created.
| customer | integer| The intended recipient of the shipment.  This `id` can be obtained from the Toolbox Genomics API after Customer creation.
| recipient_address | Address | The destination of the shipment.
| recipient_phone | string |
| recipient_name | string |
| sku | string | The SKU of the DNA Collection Kit for shipment.
| quantity | integer | The quantity of the item for shipment.
| is_replacement | bool | Indicates whether or not the requested shipment is intended as a replacement kit for the Customer.
| notes | string | Delivery notes.
| tracking_no | string | tracking number of the shipment.

#### Example Request

```
GET /api/v1/customer-shipments/70/
Host: staging.partners.toolboxgenomics.com
Content-Type: application/json

```

#### Example Response

```
HTTP/1.0 200 OK 
Content-Type: application/json

{
  "id": 70,
  "created_at": "2017-11-24 10:00:00",
  "recipient_address": {
    "line_1": "2950 Buskirk Avenue",
    "line_2": "Suite 300",
    "city": "Walnut Creek",
    "state": "CA",
    "postal_code": "94597"
    "country: "US"
  },
  "recipient_phone": "(415)722-4393",
  "recipient_name": "Jon Snow",
  "sku": "PT-Kit-1",
  "tracking_no": null
  "quantity": 1,
  "customer": 319,
  "is_replacement": False

}
```

<br />

## List all Customer Shipments
### GET `/api/v1/customer-shipments/ `

Retrieve the list of all Customer Shipments.

| Attribute Name | Data Type | Description
|:---|:---|:---
| id | integer| System generated `id` of Toolbox Genomics API after Shipment creation.
| created_at | date | The datetime Shipment is created.
| customer | integer| The intended recipient of the shipment.  This `id` can be obtained from the Toolbox Genomics API after Customer creation.
| recipient_address | Address | The destination of the shipment.
| recipient_phone | string |
| recipient_name | string |
| sku | string | The SKU of the DNA Collection Kit for shipment.
| quantity | integer | The quantity of the item for shipment.
| is_replacement | bool | Indicates whether or not the requested shipment is intended as a replacement kit for the Customer.
| notes | string | Delivery notes.
| tracking_no | string | tracking number of the shipment.

#### Example


##### Request

```
GET /api/v1/customer-shipments/
Host: staging.partners.toolboxgenomics.com
Content-Type: application/json

```

##### Success Response

```
HTTP/1.0 200 OK 
Content-Type: application/json

[
    {
      "id": 70,
      "created_at": "2017-11-24 10:00:00",
      "recipient_address": {
        "line_1": "2950 Buskirk Avenue",
        "line_2": "Suite 300",
        "city": "Walnut Creek",
        "state": "CA",
        "postal_code": "94597"
        "country: "US"
      },
      "recipient_phone": "(415)722-4393",
      "recipient_name": "Jon Snow",
      "sku": "pt-kit-1",
      "tracking_no": null
      "quantity": 1,
      "customer": 319,
      "is_replacement": false
    },
    {
      "id": 71,
      "created_at": "2017-11-24 10:01:00",
      "recipient_address": {
        "line_1": "2950 Buskirk Avenue",
        "line_2": "Suite 300",
        "city": "Walnut Creek",
        "state": "CA",
        "postal_code": "94597"
        "country: "US"
      },
      "recipient_phone": "(415)722-4393",
      "recipient_name": "Jon Snow",
      "sku": "pt-kit-1",
      "tracking_no": null
      "quantity": 1,
      "customer_id": 320,
      "is_replacement": false

    },
]
```
