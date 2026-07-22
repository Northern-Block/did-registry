# DID Registry

This repository stores DID (Decentralized Identifier) documents for `did:web` and `did:webvh` methods.

## Purpose

It acts as a public registry of DID documents that are resolved over HTTPS, following the `did:web` and `did:webvh` DID method specifications.

## Structure

Documents are organized first by environment, then by DID path, mirroring how they are resolved over HTTPS:

```
<environment>/
  <did-path>/
    did.json                    # did:web document
    .well-known/
      did.json                  # did:web document for the root identifier of this path
```

- `<environment>` — e.g. `dev`, `test`, `prod` — keeps documents for different deployment environments isolated from one another.
- `<did-path>` — the path segment(s) of the DID identifier (as used in `did:web:<domain>:<path>`).
- `did.json` — the resolved DID document for that path.
- `.well-known/did.json` — the resolved DID document when the identifier has no path segment (root domain identifier), per the `did:web` spec.

For `did:webvh` identifiers, a `did.jsonl` log file sits alongside `did.json` in the same folder, recording the verifiable version history of the document.

## Adding a new DID document

1. Create `<environment>/<did-path>/` matching the intended DID identifier (or `<environment>/.well-known/` for a root identifier).
2. Add the resolved `did.json` (and `did.jsonl` log for `did:webvh`).
3. Validate the document against the relevant DID method specification before committing.

## References

- [DID Core Specification](https://www.w3.org/TR/did-core/)
- [did:web Method Specification](https://w3c-ccg.github.io/did-method-web/)
- [did:webvh Method Specification](https://identity.foundation/didwebvh/)
