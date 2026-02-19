# Data Tables

## List Data Tables

**Endpoint**
```
GET https://admin.memberstack.com/v2/data-tables
```

**Example Response**
```json
{
  "data": {
    "tables": [
      {
        "id": "tbl_cm1abc123def456",
        "key": "products",
        "name": "Products",
        "createRule": "AUTHENTICATED",
        "readRule": "PUBLIC",
        "updateRule": "AUTHENTICATED_OWN",
        "deleteRule": "ADMIN_ONLY",
        "createdAt": "2024-01-15T10:30:00.000Z",
        "updatedAt": "2024-01-20T14:45:00.000Z",
        "fields": [
          {
            "id": "cm2xyz789ghi012abc",
            "key": "name",
            "name": "Product Name",
            "type": "TEXT",
            "required": true,
            "defaultValue": null,
            "tableOrder": 0,
            "referencedTableId": null
          },
          {
            "id": "cm3def456jkl789xyz",
            "key": "price",
            "name": "Price",
            "type": "DECIMAL",
            "required": true,
            "defaultValue": null,
            "tableOrder": 0,
            "referencedTableId": null
          },
          {
            "id": "cm4ghi789mno012def",
            "key": "category",
            "name": "Category",
            "type": "REFERENCE",
            "required": false,
            "defaultValue": null,
            "tableOrder": 0,
            "referencedTableId": "tbl_cm5cat001pqr345",
            "referencedTable": {
              "id": "tbl_cm5cat001pqr345",
              "key": "categories",
              "name": "Categories"
            }
          }
        ]
      }
    ]
  }
}
```

---

## Get Data Table

**Endpoint**
```
GET https://admin.memberstack.com/v2/data-tables/:tableKey
```

**URL Parameters**

Replace `:tableKey` with either:
- Table key (e.g., `products`)
- Table ID (e.g., `tbl_cm1abc123def456`)

**Example Response**
```json
{
  "data": {
    "id": "tbl_cm1abc123def456",
    "key": "products",
    "name": "Products",
    "createRule": "AUTHENTICATED",
    "readRule": "PUBLIC",
    "updateRule": "AUTHENTICATED_OWN",
    "deleteRule": "ADMIN_ONLY",
    "createdAt": "2024-01-15T10:30:00.000Z",
    "updatedAt": "2024-01-20T14:45:00.000Z",
    "fields": [
      {
        "id": "cm2xyz789ghi012abc",
        "key": "name",
        "name": "Product Name",
        "type": "TEXT",
        "required": true,
        "defaultValue": null,
        "tableOrder": 0,
        "referencedTableId": null
      }
    ]
  }
}
```

---

## Create Data Record

**Endpoint**
```
POST https://admin.memberstack.com/v2/data-tables/:tableKey/records
```

**URL Parameters**

Replace `:tableKey` with the table key or ID

**Request Body**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| data | object | Yes | Object containing field key-value pairs |

**Example Response**
```json
{
  "data": {
    "id": "cm7new123vwx901def",
    "tableKey": "products",
    "data": {
      "name": "Premium Widget",
      "price": 29.99,
      "inStock": true,
      "category": "cm6cat001stu678abc"
    },
    "createdAt": "2024-01-25T09:15:00.000Z",
    "updatedAt": "2024-01-25T09:15:00.000Z",
    "internalOrder": 12345
  }
}
```

---

## Update Data Record

**Endpoint**
```
PUT https://admin.memberstack.com/v2/data-tables/:tableKey/records/:recordId
```

**URL Parameters**

- Replace `:tableKey` with the table key or ID
- Replace `:recordId` with the record ID

**Request Body**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| data | object | Yes | Object containing field key-value pairs to update (cannot be empty) |

**Example Response**
```json
{
  "data": {
    "id": "cm8abc123yza234ghi",
    "tableKey": "products",
    "data": {
      "name": "Premium Widget",
      "price": 39.99,
      "inStock": false,
      "category": "cm6cat001stu678abc"
    },
    "createdAt": "2024-01-25T09:15:00.000Z",
    "updatedAt": "2024-01-26T11:30:00.000Z",
    "internalOrder": 12345
  }
}
```

---

## Delete Data Record

**Endpoint**
```
DELETE https://admin.memberstack.com/v2/data-tables/:tableKey/records/:recordId
```

**URL Parameters**

- Replace `:tableKey` with the table key or ID
- Replace `:recordId` with the record ID

**Example Response**
```json
{
  "data": {
    "id": "cm8abc123yza234ghi",
    "tableKey": "products",
    "data": {
      "name": "Premium Widget",
      "price": 39.99,
      "inStock": false,
      "category": "cm6cat001stu678abc"
    },
    "createdAt": "2024-01-25T09:15:00.000Z",
    "updatedAt": "2024-01-26T11:30:00.000Z",
    "internalOrder": 12345
  }
}
```

---

## Query Data Records

**Endpoint**
```
POST https://admin.memberstack.com/v2/data-tables/:tableKey/records/query
```

**URL Parameters**

Replace `:tableKey` with the table key or ID

**Request Body**

| Parameter | Type | Description |
| --- | --- | --- |
| query.findMany | object | Query multiple records (mutually exclusive with findUnique) |
| query.findUnique | object | Query a single record by ID (mutually exclusive with findMany) |

**Query Options (findMany)**

| Option | Type | Description |
| --- | --- | --- |
| where | object | Filter conditions |
| include | object | Include related records or counts |
| select | object | Select specific fields (cannot use with include) |
| orderBy | object \| array | Sort results |
| take | number | Limit number of results (max 100) |
| skip | number | Offset pagination (max 10000) |
| after | number \| string | Cursor-based pagination (cannot use with skip) |
| _count | boolean | Return only the count of matching records |

**Where Operators**

| Operator | Description | Example |
| --- | --- | --- |
| equals | Exact match | `{ price: { equals: 29.99 } }` |
| not | Not equal | `{ status: { not: 'archived' } }` |
| in | In array | `{ status: { in: ['active', 'pending'] } }` |
| notIn | Not in array | `{ status: { notIn: ['deleted'] } }` |
| lt | Less than | `{ price: { lt: 100 } }` |
| lte | Less than or equal | `{ price: { lte: 100 } }` |
| gt | Greater than | `{ price: { gt: 50 } }` |
| gte | Greater than or equal | `{ price: { gte: 50 } }` |
| contains | Contains substring | `{ name: { contains: 'widget' } }` |
| startsWith | Starts with | `{ name: { startsWith: 'Premium' } }` |
| endsWith | Ends with | `{ name: { endsWith: 'Pro' } }` |

Logical operators `AND`, `OR`, and `NOT` can be used to combine conditions.

**Example Response (findMany)**
```json
{
  "data": {
    "records": [
      {
        "id": "cm8abc123yza234ghi",
        "internalOrder": 12345,
        "createdAt": "2024-01-25T09:15:00.000Z",
        "updatedAt": "2024-01-26T11:30:00.000Z",
        "data": {
          "name": "Premium Widget",
          "price": 29.99,
          "inStock": true
        }
      }
    ],
    "pagination": {
      "hasMore": true,
      "limit": 20,
      "endCursor": 12345
    }
  }
}
```

**Example Response (findUnique)**
```json
{
  "data": {
    "record": {
      "id": "cm8abc123yza234ghi",
      "internalOrder": 12345,
      "createdAt": "2024-01-25T09:15:00.000Z",
      "updatedAt": "2024-01-26T11:30:00.000Z",
      "data": {
        "name": "Premium Widget",
        "price": 29.99,
        "inStock": true,
        "category": {
          "id": "cm6cat001stu678abc",
          "data": {
            "name": "Electronics"
          }
        }
      }
    }
  }
}
```

**Example Response (_count)**
```json
{
  "data": {
    "_count": 42
  }
}
```

---

## Field Types

| Type | Description |
| --- | --- |
| TEXT | String values |
| TEXT_UNIQUE | String values with unique constraint |
| NUMBER | Numeric values |
| DECIMAL | Decimal/currency values |
| BOOLEAN | True/false values |
| DATE | Date and time values |
| EMAIL | Email address values |
| URL | URL values |
| REFERENCE | Single record relationship |
| REFERENCE_MANY | Multiple record relationships |
| MEMBER_REFERENCE | Single member relationship |
| MEMBER_REFERENCE_MANY | Multiple member relationships |

---

## Common Errors

| Status | Error | Description |
| --- | --- | --- |
| 400 | Table key is required | Missing table key in URL |
| 400 | Record ID is required | Missing record ID in URL |
| 400 | data must be an object | Invalid data format in request body |
| 400 | data cannot be empty | Update request with empty data object |
| 400 | Query parameter is required | Missing query in request body |
| 400 | Invalid table key or ID format | Table key contains invalid characters |
| 400 | take must be between 1 and 100 | Query take value out of range |
| 400 | Either query.findMany or query.findUnique parameter is required | Missing query type |
| 400 | Cannot specify both query.findMany and query.findUnique | Both query types provided |
| 400 | query.findUnique requires where.id | Missing id in findUnique where clause |
| 404 | Data table not found | Table doesn't exist or wrong app |
| 404 | Data record not found | Record doesn't exist |
| 404 | Record not found | findUnique query returned no results |

**Error Response Format**
```json
{
  "code": "error-code",
  "message": "Error description here"
}
```
