---
appliesTo:
  - type: capability
    id: browse-world-stations
  - type: capability
    id: browse-country
  - type: capability
    id: search-stations
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: code
    role: implementation
    target: RadioAtlas.qml#browseCountry
  - kind: code
    role: implementation
    target: RadioAtlas.qml#previewSearch
---

# Known stations show before the directory answers

The World list, a country's list and search results first show what the session's catalog already holds, at once; Radio Browser's answer then extends or replaces them. The Listener never waits on the network to see something.
