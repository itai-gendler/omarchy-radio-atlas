---
kind: edge
routes:
  window: Radio Atlas window
steps:
  - text: The Listener presses Stop while a random pick is still loading or a station is still starting
    kind: actor
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
  - text: The Product cancels the pending tuning or start so that no station begins playing afterwards
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Current station] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: radio-player#cancel_pending_plays
---

# Stop while tuning

## Trigger

The Listener changes their mind before the station has started.

## Outcome

The pending random tuning or station start is abandoned, including before any audio plays; what was playing before, if anything, is stopped too.
