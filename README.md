# NVDA Clipboard vendored dependencies

This submodule carries the pinned runtime dependencies used by the NVDA
Clipboard add-on. It is checked out under `addon/globalPlugins/nvdaClipboard/_vendor`
and is not meant to be installed globally.

## Contents

- `msal/` from MSAL for Python 1.37.0.
- `jwt/` from PyJWT 2.13.0.
- `licenses/` with the bundled package license texts.
- `_native/` with arch-specific binaries and notices.

## Local patch

`msal/oauth2cli/assertion.py` uses a relative import for the bundled PyJWT
package:

```python
from ... import jwt
```

This keeps the add-on self-contained.

## Update rule

Refresh the Python trees from their tagged releases, update `_native/`, keep
the relative PyJWT import, and run the add-on's storage and OneDrive checks
before moving the parent repository's submodule pointer.
