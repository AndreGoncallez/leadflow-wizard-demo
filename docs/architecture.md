This architecture separates responsibilities between interface, automation logic, and data storage.

---

# 2. Frontend Layer

The frontend is responsible for guiding users through structured intake flows.

Technologies used:

- React
- Vite
- TypeScript
- TailwindCSS
- shadcn-ui
- Framer Motion

Responsibilities of this layer:

- present service request options
- collect structured input
- validate form fields
- generate normalized request payloads
- send data to automation pipelines

The frontend does **not contain business logic** related to request routing.

---

# 3. Intake Flow Logic

The wizard organizes requests into three primary flows.

### Flow A — New Lead / Interest

Used for users interested in services or courses.

Purpose:

- capture potential leads
- route to commercial or intake teams

---

### Flow B — Active User Support

Used by users who already have an existing relationship with the organization.

Purpose:

- route support requests to internal departments

---

### Flow C — Corporate Requests

Used by companies requesting services such as training or consulting.

Purpose:

- route corporate opportunities to business development teams

---

# 4. Webhook Integration

Once the form is completed, the frontend sends a POST request to a webhook endpoint.

Example payload:

```json
{
  "profile": "new_user",
  "user_status": "new",
  "interest_area": "Information Technology",
  "contact": {
    "name": "User Name",
    "whatsapp": "5500000000000"
  },
  "message": "Example message."
}

```

This payload is intentionally structured to simplify downstream automation.

## 5. Automation Layer
   The automation layer is designed to be handled by a workflow engine such as n8n.

### Responsibilities:

  - receive webhook events
  - normalize incoming data
  - classify request types
  - route requests to the correct operational team
  - store data for analytics

### Possible automation actions include:

  - sending notifications
  - creating tickets
  - storing leads in databases
  - generating analytics events

## 6. Data Layer
  The system is designed to support a structured data model.
  Conceptual entities include:

## Leads
  Stores incoming contact requests.

  Example fields:

  - name
  - contact
  - interest_area
  - message
  - created_at

## Companies
  Stores corporate service requests.

Example fields:

  - company_name
  - contact_name
  - company_identifier
  - request_description
  
## Requests

Stores operational service requests.

Example fields:

  - request_type
  - sector
  - description
  - status
  - created_at

### 7. Storage Options
  During the prototype phase, the system can use simple storage layers such as:

  - Google Sheets
  - Airtable
  - lightweight databases
    
For production environments, the architecture supports:

  - PostgreSQL
  - Supabase
  - cloud databases

### 8. Observability and Metrics
  Structured request intake enables future analytics capabilities.

Possible metrics include:

  - number of incoming requests
  - request types distribution
  - lead conversion rates
  - response time metrics

This enables operational insights and process optimization.

### 9. Security Considerations
This public repository contains an anonymized demonstration version of the system.

Security principles applied:

  - no production webhook endpoints exposed
  - no personal data included
  - no credentials stored in the repository
  - all payload examples use fictional data

### 10. Scalability Considerations
The architecture is intentionally modular.

  - Possible extensions include:
  - message queue integration
  - event-driven workflows
  - CRM integration
  - automated ticket generation
  - analytics dashboards

This design allows the intake system to scale from small prototypes to enterprise environments.

### 11. Summary
LeadFlow Wizard demonstrates how structured intake interfaces can integrate with automation workflows to create scalable request routing systems.

The architecture emphasizes:

  - separation of concerns
  - structured data intake
  - automation-driven processing
  - extensible backend integrations

