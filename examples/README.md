## Workflow: Clasificador de Siniestros (importable)

Archivo: `examples/claims-classifier.workflow.json`

Instrucciones de importación:
- Abre n8n → Workflows → Import from File → selecciona `claims-classifier.workflow.json`.
- Edita el nodo "Webhook Intake" y copia la URL (test/prod) para tus pruebas.
- Configura:
  - OPENAI_API_KEY en variables de entorno del contenedor n8n.
  - Credenciales Postgres en n8n (o usa `N8N_PG_CREDENTIAL_ID`).
  - Airtable: `AIRTABLE_API_KEY` y `AIRTABLE_BASE_ID` (tabla `Clientes`).
- Sustituye los nodos "stub" por OCR real (AWS Textract o Google Document AI) si lo necesitas.

Flujo:
Webhook → Normalize → (Download stub) → (OCR stub) → OpenAI → Parse → Guardrails → If Review → [Wait/Webhook] → Merge → Postgres → Airtable → Respond

