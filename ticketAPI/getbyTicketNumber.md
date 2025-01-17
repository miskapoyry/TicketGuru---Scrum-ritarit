## Show one ticket

**Method** : `GET`

**URL** : `/api/tickets/{ticketNumber}`

**Description** : Retrieves a specific ticket based on the provided ticketId. The response includes detailed information about the ticket, including the event, ticket type, sale details, and whether the ticket has been used.

**Successfull Response** :

- Status Code: `200 OK`

**Response Body** : 

A ticket objects containing the following fields:

```json
{
  "ticketId": 1,
  "ticketNumber": "TICKET-1001",
  "eventId": 1,
  "eventName": "Tech Conference 2024",
  "ticketTypeId": 1,
  "saleId": 1,
  "saleTimestamp": "2024-03-01T08:00:00.000+00:00",
  "usedTimestamp": null,
  "quantity": 1,
  "price": 99.99,
  "used": false
}

```

### Field Descriptions
- **`ticketId`**: Unique identifier for the ticket.
- **`ticketNumber`**: The alphanumeric identifier assigned to the ticket.
- **`eventId`**: Identifier for the associated event.
- **`eventName`**: The name of the associated event.
- **`ticketTypeId`**: Identifier for the type of ticket (e.g., general admission, VIP).
- **`saleId`**: Identifier for the sale transaction related to this ticket.
- **`saleTimestamp`**: Date and time when the ticket was purchased, in ISO 8601 format.
- **`usedTimestamp`**: Date and time when the ticket was used (if applicable), in ISO 8601 format. This field will be `null` if the ticket has not been used.
- **`quantity`**: Quantity, which will always be 1 for a single ticket retrieval.
- **`price`**: The price of the ticket.
- **`used`**: Boolean indicating whether the ticket has been used (`true`) or not (`false`).

**Error Responses** :

**Condition: This occurs if no ticket is found with the given ticketId**

Code: `404 Not Found`

Error Example:

```json
{
  "message": "Ticket not found",
  "status": 404,
  "timestamp": "2024-11-03T14:25:16.3762063",
  "path": "uri=/api/tickets/35"
}
```