# Member Actions

## List Members

**Endpoint**
```
GET https://admin.memberstack.com/members
```

**URL Parameters**

| Parameter | Type | Description |
| --- | --- | --- |
| after | number | The endCursor after which the querying should start |
| order | string | The order in which members should be queried (ASC or DESC, default: ASC) |
| limit | number | The maximum number of members to return (default: 50, max: 200) |

**Example Response**
```json
{
  "totalCount": 25,
  "endCursor": 456,
  "hasNextPage": true,
  "data": [
    {
      "id": "mem_abc123",
      "createdAt": "2022-05-19T18:57:35.143Z",
      "lastLogin": "2022-05-19T18:57:35.143Z",
      "auth": {
        "email": "john@example.com"
      },
      "customFields": {
        "country": "Germany"
      },
      "metaData": {
        "avatar": "photo.png"
      },
      "loginRedirect": "/welcome",
      "permissions": ["view:basic:workouts"],
      "planConnections": [
        {
          "id": "con_xyz789",
          "status": "ACTIVE",
          "planId": "pln_123abc",
          "type": "FREE",
          "payment": null
        }
      ]
    }
  ]
}
```

---

## Get Member

**Endpoint**
```
GET https://admin.memberstack.com/members/:id_or_email
```

**URL Parameters**

Replace `:id_or_email` with either:
- Member ID (starts with `mem_`)
- Member email address (URL-encoded)

**Example Response**
```json
{
  "data": {
    "id": "mem_abc123",
    "auth": {
      "email": "user@example.com"
    },
    "createdAt": "2022-05-19T18:57:35.143Z",
    "lastLogin": "2022-05-19T18:57:35.143Z",
    "metaData": {
      "language": "English"
    },
    "customFields": {
      "country": "United States",
      "firstName": "John"
    },
    "permissions": ["view:content"],
    "loginRedirect": "/dashboard",
    "planConnections": [
      {
        "id": "con_xyz789",
        "status": "ACTIVE",
        "planId": "pln_123abc",
        "type": "FREE",
        "payment": null
      }
    ]
  }
}
```

---

## Create Member

**Endpoint**
```
POST https://admin.memberstack.com/members
```

**Request Body**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| email | string | Yes | The member's email address |
| password | string | Yes | The member's password |
| plans | array | No | Array of plan objects: `[{'planId': 'pln_abc'}]` |
| customFields | object | No | Custom fields for the member |
| metaData | object | No | Metadata for the member |
| json | object | No | JSON data for the member |
| loginRedirect | string | No | URL to redirect to after login |

**Example Response**
```json
{
  "data": {
    "id": "mem_new123",
    "auth": {
      "email": "john@example.com"
    },
    "createdAt": "2023-01-19T12:34:56.789Z",
    "metaData": {
      "source": "API"
    },
    "customFields": {
      "firstName": "John",
      "lastName": "Doe",
      "country": "USA"
    },
    "json": {
      "preferences": {
        "theme": "dark",
        "notifications": true
      }
    },
    "permissions": [],
    "loginRedirect": "/dashboard",
    "planConnections": [
      {
        "id": "con_new456",
        "status": "ACTIVE",
        "planId": "pln_abc123",
        "type": "FREE",
        "payment": null
      }
    ]
  }
}
```

---

## Update Member

**Endpoint**
```
PATCH https://admin.memberstack.com/members/:id
```

**URL Parameters**

Replace `:id` with the member's ID (starts with `mem_`)

**Request Body**

| Parameter | Type | Description |
| --- | --- | --- |
| email | string | Update the member's email address |
| customFields | object | Update custom fields |
| metaData | object | Update metadata |
| json | object | Update JSON data |
| loginRedirect | string | Update login redirect URL |

**Example Response**
```json
{
  "data": {
    "id": "mem_abc123",
    "auth": {
      "email": "john.updated@example.com"
    },
    "createdAt": "2022-05-19T18:57:35.143Z",
    "lastLogin": "2022-05-19T18:57:35.143Z",
    "metaData": {
      "lastUpdated": "2023-01-20"
    },
    "customFields": {
      "firstName": "John",
      "lastName": "Updated",
      "country": "Canada"
    },
    "permissions": ["view:content"],
    "loginRedirect": "/dashboard",
    "planConnections": [
      {
        "id": "con_xyz789",
        "status": "ACTIVE",
        "planId": "pln_123abc",
        "type": "FREE",
        "payment": null
      }
    ]
  }
}
```

---

## Delete Member

**Endpoint**
```
DELETE https://admin.memberstack.com/members/:id
```

**URL Parameters**

Replace `:id` with the member's ID (starts with `mem_`)

**Request Body** (Optional)

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| deleteStripeCustomer | boolean | false | Delete the associated Stripe customer |
| cancelStripeSubscriptions | boolean | false | Cancel the associated Stripe subscriptions |

**Example Response**
```json
{
  "data": {
    "id": "mem_abc123"
  }
}
```

---

## Add a Free Plan

**Endpoint**
```
POST https://admin.memberstack.com/members/:id/add-plan
```

**URL Parameters**

Replace `:id` with the member's ID (starts with `mem_`)

**Request Body**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| planId | string | Yes | The ID of the free plan to add (starts with `pln_`) |

**Example Response**

A successful request returns a `200` status code with no response body.

---

## Remove a Free Plan

**Endpoint**
```
POST https://admin.memberstack.com/members/:id/remove-plan
```

**URL Parameters**

Replace `:id` with the member's ID (starts with `mem_`)

**Request Body**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| planId | string | Yes | The ID of the free plan to remove (starts with `pln_`) |

**Example Response**

A successful request returns a `200` status code with no response body.
