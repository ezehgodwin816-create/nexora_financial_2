NEXORA FINANCIAL — ADMIN VERIFICATION STATUS UPDATE

This package keeps the corrected register.html and updates admin.html.

Admin customer cards now include:
- Identity verification status
- Document status
- Number of documents submitted
- Last verification/document update
- Verification notes

The admin UI reads these optional fields when returned by the
admin_get_customers RPC:
- verification_status
- identity_verification_status
- kyc_status
- document_status
- documents_status
- documents_count
- document_count
- uploaded_documents_count
- verification_updated_at
- documents_updated_at
- kyc_updated_at
- verification_notes
- kyc_notes

IMPORTANT:
The admin page intentionally displays status/metadata rather than raw
SSNs, passport numbers, licence numbers, or identity-document contents.

For the new status boxes to show real values, the database/RPC must return
the corresponding status fields. If those fields are absent, the UI safely
shows "Not submitted" or "—".
