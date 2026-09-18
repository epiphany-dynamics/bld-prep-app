# Security

## Data handling

This demo is designed to run locally in the browser. It has no server-side upload endpoint, authentication flow, or credential store.

Do not upload live customer, employee, location, infrastructure, or inspection data to a public deployment. Use synthetic fixtures for demos and screenshots.

## Reporting a suspected secret

If you find a credential, token, private key, or other sensitive value in this repository, do not open a public issue with the value. Contact Epiphany Dynamics privately with the file path and commit reference, leaving the secret itself redacted.

If a credential is discovered, revoke or rotate it first, then remove it from every reachable commit before republishing the repository.
