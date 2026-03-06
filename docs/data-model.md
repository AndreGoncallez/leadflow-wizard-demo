# Data Model

The intake system was designed around four main entities.

## Leads

Initial contact data collected through the wizard.

Fields example:

- name
- contact
- interest_area
- message
- created_at

## Companies

Corporate entities requesting services.

Fields example:

- company_name
- contact_name
- company_identifier
- request_description

## Requests

Structured operational requests generated from intake flows.

Fields example:

- request_type
- sector
- description
- status
- created_at

## Conversions

Records generated when a lead becomes an enrolled student or confirmed service client.
