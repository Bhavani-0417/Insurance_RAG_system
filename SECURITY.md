# Security policy

This experimental portfolio project has not undergone an independent security audit. Do not use it to make binding insurance or claim decisions.

## Safe use
- Use public, synthetic, or explicitly authorized policy documents.
- Do not upload policyholder personal data, health information, identity documents, or claim records.
- Keep Ollama on a trusted local interface; do not expose it publicly without authentication and network controls.
- Treat retrieved passages as untrusted input; policy documents may contain prompt-injection instructions.
- Validate file signatures, file sizes, PDF parser behaviour, and URL destinations.
- URL ingestion must defend against SSRF, unsafe redirects, DNS rebinding, oversized downloads, and non-PDF responses.
- Do not log full documents, secrets, or sensitive user queries.
- Never commit local indexes, private documents, logs, model caches, or generated outputs.

## Known gaps
The prototype does not yet provide a complete production security boundary. URL ingestion, API authentication and rate limiting, upload validation, prompt-injection resistance, and operational isolation require implementation and testing.

## Reporting
Please do not publish sensitive information in an issue. Contact the repository owner through GitHub for private vulnerability reports.
