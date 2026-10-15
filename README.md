# Public developer packet v0.5
Read START_HERE.md first. Load the files, acknowledge scope, then wait for a question.

Files: START_HERE.md, functions.csv, function_args.csv, layers.csv, fields.csv, service.wsdl, EXAMPLES_AND_LIMITS.md, TEST_PROMPTS.md, MANIFEST.json.

The function catalog and arguments were exported October 4, 2026; WSDL came from public GISN that day. Resource/field CSVs are historical September 20 snapshots (571 resources, 7,234 field rows); their source host was not recorded. Treat them as discovery clues, not a verified inventory of publicly accessible resources. Verify public availability before recommending an actual call. This packet does not refresh files or run calls on startup.

Public requests only. Provide complete cURL/Postman examples. SOAP execution requires explicit user approval for the specific call or bounded set. No private conversation archive or internal endpoint instructions are included.

Conceptual argument groups and exact WSDL wire names differ; use function_args.csv's wire_arguments and service.wsdl. Catalog observations are evidence for recorded cases, not universal success claims. Keep user enrichment separate from source catalogs and report persistence honestly.

This is a separate reduced derivative of v0.4. It has not been validated in the receiving Copilot environment. Web API/Swagger changes from October 6 are not incorporated into this legacy packet yet.
