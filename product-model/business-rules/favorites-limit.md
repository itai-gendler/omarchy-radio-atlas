---
appliesTo:
  - type: capability
    id: add-favorite
  - type: entity
    id: favorite
references:
  - kind: code
    role: implementation
    target: radio-state
  - kind: doc
    role: intent
    target: README.md
---

# Favorites keep up to 500 stations, newest first

Starring saves only the chosen station's own details, at the top of the favorites. Favorites hold at most 500 stations; starring a 501st drops the oldest.
