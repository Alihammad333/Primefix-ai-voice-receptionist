# API examples

The workflow uses one POST webhook and routes requests by the `action` property.

## Test connection

Request:

```json
{
  "action": "test_connection"
}
```

Response:

```json
{
  "success": true,
  "message": "PrimeFix webhook is working"
}
```

## Create a new contact

Request:

```json
{
  "action": "create_contact",
  "name": "Emily Carter",
  "phone": "+15551112222",
  "email": "emily.carter@example.com",
  "service_address": "725 Pine Street, Austin, TX"
}
```

Example response:

```json
{
  "success": true,
  "message": "Contact created successfully",
  "contact_id": "recXXXXXXXXXXXXXX"
}
```

When the phone number already exists, the response keeps the same shape and returns `Contact already exists` with the existing record ID.

## Book an appointment

Request:

```json
{
  "action": "book_appointment",
  "contact_id": "recXXXXXXXXXXXXXX",
  "service_type": "HVAC",
  "issue_description": "The air conditioner is making a loud noise.",
  "appointment_time": "2026-10-12T14:00:00+05:00"
}
```

Example response:

```json
{
  "success": true,
  "message": "Appointment confirmed successfully",
  "appointment_record_id": "recYYYYYYYYYYYYYY",
  "appointment_id": "APT-1790105730185",
  "status": "Confirmed",
  "calendar_event_id": "example-calendar-event-id"
}
```

Record and event IDs above are placeholders or synthetic examples.
