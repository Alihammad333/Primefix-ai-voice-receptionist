# Airtable schema

Create one Airtable base named `PrimeFix Voice Receptionist` with the following tables.

## Contacts

| Field | Type | Purpose |
| --- | --- | --- |
| `name` | Single line text | Customer's full name |
| `phone` | Phone or single line text | Duplicate lookup key |
| `email` | Email | Optional customer email |
| `service_address` | Long text | Address where service is required |
| `created_at` | Created time | Audit timestamp |
| `updated_at` | Last modified time | Latest record update |
| `Appointments` | Linked records | Reverse link from Appointments |

## Appointments

| Field | Type | Purpose |
| --- | --- | --- |
| `appointment_id` | Single line text | Human-readable ID such as `APT-...` |
| `contact` | Link to Contacts | Customer relationship |
| `service_type` | Single select | Plumbing, Electrical, HVAC, Appliance Repair, General Maintenance, Other |
| `issue_description` | Long text | Customer's service issue |
| `appointment_time` | Date with time | Confirmed start time |
| `status` | Single select | Requested, Confirmed, Rescheduled, Cancelled, Completed |
| `google_event_id` | Single line text | Google Calendar event reference |
| `created_at` | Created time | Audit timestamp |
| `updated_at` | Last modified time | Latest record update |

The workflow first creates an appointment as `Requested`. It changes the status to `Confirmed` only after Google Calendar successfully creates the event.
