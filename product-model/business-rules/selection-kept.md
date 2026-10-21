---
appliesTo:
  - type: capability
    id: select-station
  - type: capability
    id: browse-world-stations
  - type: capability
    id: search-stations
  - type: capability
    id: refresh-station-caches
  - type: capability
    id: record-listening-history
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: code
    role: implementation
    target: RadioAtlas.qml#setStationList
---

# Refreshed lists keep the selected station

When the World, search, country, Favorites or Recent list is refreshed, the selected station stays selected, keyboard outline included, as long as it is still listed. Track-title, volume and pause updates never move the selection.
