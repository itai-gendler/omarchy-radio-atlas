---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener presses M, the "Unmute" button or right-clicks the volume slider while the radio is muted
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Muted] }
    contexts:
      window:
        place: window::player
  - text: The Product unmutes the player and shows the volume again
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: changes, facts: [Muted] }
      - { entity: player-settings, effect: reads, facts: [Volume] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: radio-player
---

# Unmute the radio

## Trigger

The Listener wants to hear the station again.

## Outcome

The station is audible at the volume it had before muting.
