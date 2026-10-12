---
type: desktop-app
actors:
- user
references:
- kind: code
  role: implementation
  target: src/main.zi
- kind: code
  role: implementation
  target: src/platform/app_host.zi
---

# Native desktop application

The User uses the native local application with or without an account. File operations describe the inspected Linux implementation. The same local interaction contains account-dependent operations; a key is not a verified human identity.
