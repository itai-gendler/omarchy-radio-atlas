---
kind: edge
routes:
  window: Radio Atlas window
steps:
  - text: The Listener moves the volume slider
    kind: actor
    actor: listener
    entities:
      - { entity: player-settings, effect: reads, facts: [Volume] }
    contexts:
      window:
        place: window::player
  - text: The player does not accept the new volume
    kind: condition
    entities:
      - { entity: player-session, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
  - text: The Product shows "Could not change volume" and puts the slider back at the player's volume
    kind: product
    actor: listener
    entities:
      - { entity: player-settings, effect: reads, facts: [Volume] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#volumeProcess
---

# Volume cannot be changed

## Trigger

The player is busy or gone when the new volume is sent.

## Outcome

The volume stays what the player reports, and the saved volume is unchanged.
