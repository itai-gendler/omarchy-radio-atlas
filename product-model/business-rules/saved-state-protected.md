---
appliesTo:
  - type: entity
    id: favorite
  - type: entity
    id: recent-station
  - type: entity
    id: player-settings
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: code
    role: implementation
    target: radio-state#ensure_state
---

# Saved state that cannot be read is never overwritten

When the saved favorites, history and settings are malformed, oversized or hold too many entries, Radio Atlas refuses to write over them and reports where they are, so the Listener can back them up and repair them. A favorite or history change that cannot be saved leaves the saved stations as they were.
