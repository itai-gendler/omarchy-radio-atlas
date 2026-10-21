---
kind: alternate
routes:
  window: Radio Atlas window
  bar: From the bar
steps:
  - text: The Listener changes the volume in the window or over the bar button while no player session runs
    kind: actor
    actor: listener
    entities:
      - { entity: player-settings, effect: reads, facts: [Volume] }
      - { entity: player-session, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
      bar:
        place: bar-widget::bar-button
  - text: The Product saves the volume for the next player session
    kind: product
    actor: listener
    entities:
      - { entity: player-settings, effect: changes, facts: [Volume] }
      - { entity: player-session, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
      bar:
        place: bar-widget::bar-button
references:
  - kind: code
    role: implementation
    target: radio-player#set_volume
---

# Set the volume with nothing playing

## Trigger

The Listener prepares the volume before starting a station.

## Outcome

The next station starts at the chosen volume.
