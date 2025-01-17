### Show One Ticket Type

**Method**: `GET`

**URL**: `/api/ticket-types/{id}`

**Path Parameters**: 
- `id`: Long (ID of the ticket type to retrieve)

**Successful Response**:

- Status Code: `200 OK`

**Response Body**:

```json
{
    "ticketTypeId": 2,
    "ticketTypeName": "VIP"
}

```

**Error Responses** :

**Condition: If the ticket type does not exist**

Code: ```404 Not Found``` 

Error Example:

```json
{
  "message": "TicketType with ID 234 not found",
  "status": 404,
  "timestamp": "2024-10-21T20:00:17.1611255",
  "path": "uri=/api/ticket-types/234"
}

```