---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener chooses the World tab
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: The Product lists the catalog's stations at once and highlights the playing station's country when one plays
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name, Country code, Codec, Bitrate, Tags, Location] }
      - { entity: player-session, effect: reads, facts: [Current station] }
    contexts:
      window:
        place: window::atlas
  - text: The Product fetches the world stations, from the world cache while it is fresh or else the 500 most-started stations with a location from Radio Browser
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Location, Click count] }
    contexts:
      window:
        place: window::atlas
  - text: The Product adds the stations the catalog lacks to the list and the globe, keeping the selected station selected
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name, Location] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#showWorld
  - kind: code
    role: implementation
    target: radio-fetch#refresh_world_cache
---

# Open the world list

## Trigger

The Listener wants to look across the world rather than at favorites, history or a search.

## Outcome

The World list holds the session's catalog with the selected station kept, and the globe shows its signals. A stale cache is refreshed in the background.
