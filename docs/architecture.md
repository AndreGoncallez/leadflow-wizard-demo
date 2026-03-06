# System Architecture

The LeadFlow Wizard demo represents an intake automation pipeline designed to structure incoming service requests.

Simplified architecture:

Frontend (React)
↓
Guided Intake Wizard
↓
Webhook / Automation Trigger
↓
Workflow Engine (n8n)
↓
Data Normalization
↓
Storage Layer (Spreadsheet / Database)
↓
Operational Follow-up

The public version of this repository contains only the frontend demonstration layer and documentation.
