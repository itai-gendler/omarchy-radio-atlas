---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener chooses the Favorites tab
    kind: actor
    actor: listener
    entities:
      - { entity: favorite, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
  - text: The Product lists the favorites newest first with their saved details, selects the first, and turns the globe to the playing station's country
    kind: product
    actor: listener
    entities:
      - { entity: favorite, effect: reads, facts: [Saved details, Order] }
      - { entity: player-session, effect: reads, facts: [Current station] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#showFavorites
  - kind: code
    role: implementation
    target: RadioAtlas.qml#restorePlayingCountry
---

# Open favorites

## Trigger

The Listener wants a station they starred before.

## Outcome

The Favorites list is showing without asking the directory, and its stations are on the globe. With none yet, it says "No favorites yet. Select a station and press F."
