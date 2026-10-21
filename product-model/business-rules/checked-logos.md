---
appliesTo:
  - type: capability
    id: show-station-logo
  - type: entity
    id: player-session
    facts: [Station logo]
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: code
    role: implementation
    target: radio-favicon#fetch
---

# Station logos are downloaded once and checked

A logo is downloaded once per address and kept on this computer, and only a file that is an image of at most 1 MiB is shown. Downloading runs apart from the window and never holds up the media controls.
