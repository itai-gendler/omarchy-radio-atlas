---
kind: edge
routes:
  window: Radio Atlas window
steps:
  - text: A station's stream starts playing while the saved state cannot be written
    kind: condition
    unattended: true
    entities:
      - { entity: player-session, effect: reads, facts: [Current station, Stream loaded] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
  - text: The Product leaves the history as it was and shows "Listening history could not be updated"
    kind: product
    entities:
      - { entity: recent-station, effect: reads, facts: [Order] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#historyProcess
---

# History cannot be saved

## Trigger

Playback starts while the saved state is unreadable or cannot be written.

## Outcome

Playback is unaffected; the history keeps its previous stations and the warning shows until a later update succeeds.
