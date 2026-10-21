---
availability:
  - place: window
  - place: bar-widget
domain: playback
references:
  - kind: code
    role: implementation
    target: radio-status.lua
  - kind: doc
    role: intent
    target: README.md
---

# Keep a failed station selected

When a station's stream disconnects or cannot be played, hold that station with the failure on show instead of reconnecting or moving on.
