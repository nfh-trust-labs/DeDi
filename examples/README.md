# Examples

Illustrative, internally-consistent examples for [publishing-dedi-files.md](../docs/publishing-dedi-files.md).
Same publisher (`example.org`) and key (`key-1`) throughout.

| File | What it is |
|---|---|
| [`well-known-dedi.json`](well-known-dedi.json) | The publisher's `/.well-known/dedi.json` manifest — declares the current key and lists two registries. **The authority.** |
| [`public-keys.dedi`](public-keys.dedi) | A positive directory: presence of a record = a valid key. |
| [`revocations.dedi`](revocations.dedi) | A negative list: presence of a record = revoked. Same shape; polarity comes from the registry, not a per-record field. |
| [`domains.txt`](domains.txt) | The discovery list — just publisher domains. Vouches for nobody. |

Verify any `.dedi` file by: (1) checking its `proof` against its embedded `publisher.key`, then
(2) confirming that key appears in `keys` of `well-known-dedi.json`.

> **Not cryptographically valid.** The `jws` and `digest` values are placeholders (marked
> `ILLUSTRATIVE_...` where applicable) to show *shape*, not real signatures. A real file carries a
> detached JWS over the JCS-canonicalized document, signed with the publisher's private key.

> **Temporary schema URLs.** The `schema` / `$id` URLs point at the repo's `main` branch, which is
> mutable. Before release they must be pinned to a version tag or commit SHA (see §10 of the spec).
