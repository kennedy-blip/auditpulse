# AuditPulse

Immutable audit log explorer, cryptographic SHA-256 hash-chain verifier, and security forensics studio.

## Stack
React 18, TypeScript, Vite 6, Tailwind CSS v4, Vercel Node Serverless Functions.

## Local development

```bash
npm install
npm run build
npx vercel dev
```

Run `npm run dev` for the Vite-only frontend demo; it loads a labelled local dataset when the API is unavailable.

## API
- GET /api/audit-logs — chronological event ledger and chain verification
- GET /api/audit-logs?verify=true — verification report
- GET /api/audit-logs/verify — dedicated verification endpoint
- POST /api/audit-logs — append actor, action, resource, severity, metadata
- POST /api/tamper-sim — mutate an event and return chain verification

## Deployment and integrity notes
Import this repository into Vercel using the repository root. The audit store is intentionally in-memory for demonstration: Vercel functions are ephemeral and may run in separate instances, so this is not durable compliance storage. For production evidence, replace the store with a durable database, add authentication/authorization and rate limits, and use protected signing and retention controls. A plain hash chain cannot prove non-repudiation against an attacker able to rewrite the entire ledger.
