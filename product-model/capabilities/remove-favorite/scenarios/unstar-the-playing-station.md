---
kind: alternate
routes:
  window: Radio Atlas window
steps:
  - text: The Listener presses the filled star beside the playing station in the player
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Current station] }
      - { entity: station, effect: reads, facts: [Name] }
    contexts:
      window:
        place: window::player
  - text: The Product removes the playing station from the favorites
    kind: product
    actor: listener
    entities:
      - { entity: favorite, effect: removes }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#playingFavoriteButton
---

# Unstar the playing station

## Trigger

The Listener decides the station playing no longer belongs among the favorites.

## Outcome

The station keeps playing but is no longer a favorite; the player's star is empty.
