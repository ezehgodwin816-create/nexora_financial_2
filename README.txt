NEXORA FINANCIAL — KYC CONNECTION PACKAGE

FILES
- register.html — based on the user's latest registration layout; US/UK fields are connected to KYC storage.
- admin.html — existing Admin page with a KYC & Documents section added.
- nexora_kyc_setup.sql — additive SQL migration; does not replace admin_get_customers().

IMPORTANT SETUP
1. Run nexora_kyc_setup.sql in Supabase SQL Editor.
2. In Supabase Dashboard > Storage, create a bucket named:
   nexora-kyc-documents
   Keep it PRIVATE.
3. Run the storage policies included at the bottom of the SQL file.
4. Replace the live register.html and admin.html with these versions.
5. Test with a test customer account before collecting real verification information.

SECURITY DESIGN
- Normal customer fields remain in the existing profile/Auth workflow.
- Country-specific KYC fields are stored in kyc_sensitive, protected by RLS.
- Documents are stored in a PRIVATE Storage bucket.
- Admin document viewing uses short-lived signed URLs (5 minutes).
- The Admin RPC is restricted to authenticated administrators through private.is_nexora_admin().
- No document is made public.

EMAIL CONFIRMATION NOTE
If Supabase requires email confirmation, the signup response may not include an authenticated session. In that case this version does NOT store sensitive KYC fields in localStorage or Auth metadata. The user is sent to login and should complete KYC after authentication. This is intentional for security.

IMPORTANT
The labels/fields are based on the latest code you supplied. The UK "driving licence number" input is kept as a FILE input because that is how it appeared in the supplied code; if you want it to be a text number field instead, change that input to type="text" before going live.
