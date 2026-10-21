---
availability:
  - place: window
domain: stations
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#previewSearch
  - kind: code
    role: implementation
    target: RadioAtlas.qml#search
  - kind: code
    role: implementation
    target: radio-fetch#fetch_search
  - kind: code
    role: implementation
    target: RadioModel.js#searchStations
---

# Search stations

Search by station name, country or genre: matches from the session's catalog show while typing, then the whole Radio Browser directory answers.
