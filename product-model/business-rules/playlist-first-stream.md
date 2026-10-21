---
appliesTo:
  - type: capability
    id: play-station
  - type: capability
    id: keep-failed-station-selected
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: code
    role: implementation
    target: radio-status.lua
---

# A station's playlist plays its first stream

When a station's address is an M3U or PLS playlist, only its first stream plays, and Next and Previous keep moving between stations rather than between the playlist's entries. An empty playlist is a playback failure, not a reason to move on.
