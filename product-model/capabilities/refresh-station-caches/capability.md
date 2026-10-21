---
availability:
  - place: window
domain: stations
references:
  - kind: code
    role: implementation
    target: radio-fetch#refresh_world_cache_in_background
  - kind: code
    role: implementation
    target: radio-fetch#refresh_country_cache_in_background
  - kind: code
    role: implementation
    target: RadioAtlas.qml#applyCountryCache
---

# Refresh station caches

Bring the world and country caches up to date from Radio Browser in the background once they are a day old, without holding up the list that was shown from them.
