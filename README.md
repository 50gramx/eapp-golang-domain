# EAPP Go Domain

This repository receives protobuf-generated Go sources from `eapp-system-contracts` CI.
The generated packages are split into `entities` and `services` paths so they can be
consumed directly by Go clients.

## What lives here
- Generated Go protobuf entities under `community/apps/...`
- Generated Go gRPC service stubs under `community/apps/...`
- A module root that downstream Go consumers can import once CI publishes the latest generation

## How it is updated
1. `eapp-system-contracts` generates the protobuf sources from contracts.
2. The Go CI job checks out this repository.
3. CI writes the generated sources into this module.
4. CI runs `go test ./...` to confirm the generated output is usable.
5. CI publishes a release archive for downstream consumers.

## Notes
- This repository is intentionally minimal because it is generated from contracts.
- The canonical source of truth is the contract YAML in `eapp-system-contracts`.
