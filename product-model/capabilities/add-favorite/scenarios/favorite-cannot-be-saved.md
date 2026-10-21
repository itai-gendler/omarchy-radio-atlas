---
kind: edge
routes:
  window: Radio Atlas window
steps:
  - text: The Listener stars a station
    kind: actor
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name] }
    contexts:
      window:
        place: window::atlas
  - text: The saved state cannot be read or written
    kind: condition
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: The Product shows "Favorite could not be updated" and keeps the favorites as they were
    kind: product
    actor: listener
    entities:
      - { entity: favorite, effect: reads, facts: [Order] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#stateProcess
---

# Favorite cannot be saved

## Trigger

The Listener stars a station while the saved state is unreadable or cannot be written.

## Outcome

Nothing is added; the warning shows on the globe's hint line until a later favorite change succeeds.
