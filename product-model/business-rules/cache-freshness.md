---
appliesTo:
  - type: capability
    id: refresh-station-caches
  - type: capability
    id: browse-world-stations
  - type: capability
    id: browse-country
references:
  - kind: code
    role: implementation
    target: radio-fetch#fetch_world
  - kind: code
    role: implementation
    target: radio-fetch#fetch_country
---

# World and country caches are trusted for a day

A world or country cache less than a day old is shown without asking Radio Browser. An older one is still shown at once and refreshed in the background, and a missing or unreadable one is fetched before it is shown. The caches outlive the session, so the next opening starts from them.
