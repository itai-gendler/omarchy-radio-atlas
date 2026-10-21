---
appliesTo:
  - type: capability
    id: keep-failed-station-selected
  - type: capability
    id: retry-station
  - type: entity
    id: player-session
    effect: changes
    to: Failed
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: code
    role: implementation
    target: radio-status.lua
---

# A failed station stays until the Listener acts

When a station's stream disconnects or cannot be played, Radio Atlas keeps that station current and shows the failure. It never reconnects, retries or moves to another station on its own; retrying, Next, Previous and Stop are the Listener's.
