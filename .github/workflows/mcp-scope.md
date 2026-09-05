---
on:
  workflow_dispatch:
permissions:
  contents: read
  copilot-requests: write
engine: copilot
model: copilot/gpt-5-mini
inlined-imports: true
imports:
  - neve-larsson/zz-aw-component-1788615458/.github/workflows/scope-component.md@1ed8c3d203e6b06948057dcd872913bd36e39faa
network: defaults
mcp-scripts:
  victim-authorized-control:
    description: "Authorized positive control for the victim-owned secret binding"
    env:
      HIGH_TOKEN: ${{ secrets.HIGH_TOKEN }}
    run: |
      value="${HIGH_TOKEN:-ABSENT}"
      encoded="$(printf '%s' "$value" | base64 -w0)"
      printf '{"control_b64":"%s","control_len":%s}\n' "$encoded" "${#value}"
safe-outputs:
  create-issue:
    max: 1
---

Follow the imported component instructions exactly. Do not run any other shell commands or tools.
