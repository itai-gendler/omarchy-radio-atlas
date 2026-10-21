---
kind: alternate
routes:
  window: Radio Atlas window
steps:
  - text: The Listener presses Escape in the search field, or deletes all of its text
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: The Product empties the search field and lists the catalog's stations on the World tab
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name, Country code, Codec, Bitrate, Tags, Location] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#previewSearch
---

# Clear the search

## Trigger

The Listener abandons a search.

## Outcome

The search field is empty and the World list is back, refreshed as when the World tab is chosen.
