---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener presses M, the "Mute (M)" button or right-clicks the volume slider while a player session runs
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Muted] }
    contexts:
      window:
        place: window::player
  - text: The Product mutes the player and shows the muted speaker, with "muted" in place of the volume on the bar
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: changes, facts: [Muted] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: radio-player
---

# Mute the radio

## Trigger

The Listener needs silence but wants to keep the station going.

## Outcome

The station keeps streaming silently at its saved volume. A new player session starts unmuted.

## Edge cases

- With no player session the mute button is unavailable.
