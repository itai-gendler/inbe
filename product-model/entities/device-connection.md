---
domain: account
references:
- kind: code
  role: implementation
  target: src/app/device_link_session.zi
- kind: code
  role: implementation
  target: src/screens/settings/settings_sync_account_impl.zi#SettingsDeviceLinkDraw
---

# Device connection

A local account-transfer process.

## Information kept

- **Code** — Transfer code displayed for the other device to enter or scan.
- **Direction** — Whether this desktop sends its available account credentials or receives credentials.
- **Comparison digits** — Digits presented for confirmation of the proposed transfer.
- **Expiry** — Local deadline for the active transfer process, approximately 590 seconds after starting.
- **Stage** — Current local transfer stage; Connected is a protocol observation rather than proof of completed synchronization.

## States

### Showing

The desktop presents its transfer code and waits for the other device.

### Confirm

Comparison digits are available for a human confirmation decision.

### Working

The confirmed local transfer is awaiting its protocol response.

### Received

The receiving desktop has obtained credentials for preparation or installation.

### Connected

The local transfer protocol reports success; installed keys and completed exchange on both devices are not certified.

### Failed

The local transfer reports transport, credential or node-selection failure.
