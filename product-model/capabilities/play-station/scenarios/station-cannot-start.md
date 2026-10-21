---
kind: edge
routes:
  window: Radio Atlas window
steps:
  - text: The Listener plays a station
    kind: actor
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name] }
    contexts:
      window:
        place: window::atlas
  - text: The station is no longer available, or the queue cannot be prepared or loaded
    kind: condition
    entities:
      - { entity: station, effect: reads, facts: [Stream address] }
    contexts:
      window:
        place: window::player
  - text: The Product shows "Could not play this station", or "Could not prepare this station", and leaves what was playing as it was
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#playerActionProcess
---

# Station cannot start

## Trigger

The Listener plays a station that cannot be queued.

## Outcome

The player shows the problem and nothing else changes: no queue is replaced and no player is started.
