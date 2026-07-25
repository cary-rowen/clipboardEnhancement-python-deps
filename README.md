# Clipboard Enhancement Python dependencies

This repository contains the pinned, pure-Python runtime dependencies packaged
with the [Clipboard Enhancement NVDA add-on](https://github.com/cary-rowen/clipboardEnhancement).
It is consumed as a Git submodule and is not intended to be installed globally.

## Included versions

- [MSAL for Python 1.37.0](https://github.com/AzureAD/microsoft-authentication-library-for-python/tree/1.37.0)
- [PyJWT 2.13.0](https://github.com/jpadilla/pyjwt/tree/2.13.0)

Only the importable package trees and their license texts are retained. The
directory layout is part of the add-on's private package namespace, preventing
these versions from replacing packages used by NVDA or other add-ons.

## Local compatibility patch

`msal/oauth2cli/assertion.py` imports the bundled PyJWT package relatively:

```python
from ... import jwt
```

This is intentionally different from the upstream absolute import and keeps
authentication dependencies isolated inside the add-on.

## Updating

Update both package trees from their official tagged releases, retain the
relative PyJWT import above, update the versions in this document, and run the
Clipboard Enhancement storage and OneDrive synchronization self-checks before
advancing the parent repository's submodule pointer.

The bundled packages remain under their upstream licenses; see `licenses/`.
