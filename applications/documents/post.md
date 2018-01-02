# POST /applications/{application_id}/documents

Uploads a new Document and associates it with an existing Application.

**URL** : `/applications/{application_id}/documents`

**Method** : `POST`

**Request Headers**

| Name | Value |
|:-----|:------|
|Accept|application/json|
|Authorization|[LeaseQ Auth Token](../../README.md#authorization-header)|

**Request Body**

```json
{
    "type": "string | optional | The document type - invoice, quote, contract",
    "name": "string | required | The document filename",
    "data": "string (base64 encoded) | The document data"
}
```

***Example***

```json
{
    "type": "invoice",
    "name": "Equipment Inovice.pdf",
    "data": "<base64 encoded data>"
}
```

## Success Response

**Code** : `201 CREATED`

**Response Body**

```json
{
    "document_id": "guid | The id of the uploaded document"
}
```

***Example***

```json
{
    "document_id": "00000000-0000-0000-0000-000000000000"
}
```

## Error Response

### If not authorized.

**Code** : `401 UNAUTHORIZED`

### If application is not found.

**Code** : `404 NOT FOUND`
