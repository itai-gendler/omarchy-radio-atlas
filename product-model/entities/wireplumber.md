---
kind: system
acts: external
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: code
    role: implementation
    target: radio-mpris#policy_sender
---

# WirePlumber

The desktop's audio session manager. When the output radio is playing on disappears, it pauses Radio Atlas through the media controls, and Radio Atlas tells that pause apart from one the Listener asked for.
