---
appliesTo:
  - type: capability
    id: browse-country
  - type: capability
    id: refresh-station-caches
references:
  - kind: code
    role: implementation
    target: RadioModel.js#prioritizeStations
---

# A browsed country's stations come first on the globe

When a country is browsed, its stations are placed ahead of every background station in the session's catalog, so they stay on the globe however full the catalog grows.
