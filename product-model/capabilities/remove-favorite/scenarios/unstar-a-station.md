---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener presses the filled star on a favorite station's row, or F with it selected
    kind: actor
    actor: listener
    entities:
      - { entity: favorite, effect: reads, facts: [Saved details] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
  - text: The Product removes the station from the favorites and empties its star
    kind: product
    actor: listener
    entities:
      - { entity: favorite, effect: removes }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: radio-state#write_state
---

# Unstar a station

## Trigger

The Listener no longer wants a station among the favorites.

## Outcome

The station is gone from the Favorites tab, and its star is empty wherever it is listed. On the Favorites tab, the selection moves to a neighbouring favorite.
