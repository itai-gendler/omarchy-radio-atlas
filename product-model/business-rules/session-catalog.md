---
appliesTo:
  - type: capability
    id: expand-station-catalog
  - type: capability
    id: browse-world-stations
  - type: capability
    id: close-radio-atlas
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#worldStationLimit
  - kind: code
    role: implementation
    target: manifest.json
---

# The session catalog holds at most 5,000 stations

The stations gathered for the World list and the globe stay for as long as the plugin is loaded, through closing and reopening the window, and never exceed 5,000. Stations gathered later never displace those already there, except that a browsed country's stations move to the front.
