---
appliesTo:
  - type: capability
    id: close-radio-atlas
  - type: capability
    id: stop-playback
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: code
    role: implementation
    target: radio-player
---

# Playback outlives the window

The player session runs on its own: closing the window, or the screensaver closing it, never stops or pauses the radio. Only Stop ends it.
