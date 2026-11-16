# Local data

| Directory | Contents |
| --- | --- |
| `raw/` | Original timestamped recordings and session metadata. |
| `processed/` | Derived segments, features, and split manifests. |
| `replays/` | Local recorded inputs for reproducible integration demos. |
| `../models/` | Trained artifacts and the settings/metadata needed to reproduce them. |
| `../outputs/` | Generated plots, logs, and evaluation output. |

Contents of these locations are ignored, apart from directory placeholders.
Keep personal recordings, identifiers, pairing credentials, and tokens out of
commits. Use small synthetic data in `tests/fixtures/` for shared tests; document
its format and generation alongside the fixture.

Preserve raw recordings and regenerate processed data from them. Follow the
[collection and evaluation protocol](../docs/data-and-evaluation.md) for session
metadata and held-out splits.
