---
appliesTo:
  - type: capability
    id: record-listening-history
  - type: entity
    id: recent-station
references:
  - kind: code
    role: implementation
    target: radio-state
---

# Listening history keeps the 30 latest stations

A station enters the listening history once its stream has started, not when it is chosen, and appears in it once, at the top. The history holds the 30 most recent stations.
