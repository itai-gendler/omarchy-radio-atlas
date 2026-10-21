---
appliesTo:
  - type: entity
    id: station
    facts: [Location, Approximate location]
references:
  - kind: code
    role: implementation
    target: RadioModel.js#estimatedCountryLocation
---

# Stations without coordinates are placed inside their country

A station that publishes no coordinates is shown at a point inside the largest part of its country, the same point every time, and marked "approximate location" on the globe. A station with neither coordinates nor a recognized country is listed but has no signal on the globe.
