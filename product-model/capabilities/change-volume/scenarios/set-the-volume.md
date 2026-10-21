---
kind: primary
routes:
  window: Radio Atlas window
  bar: From the bar
  media: Media controls
steps:
  - text: The Listener drags the volume slider or presses + or − in the window, scrolls over the bar button, or sets Radio Atlas's volume in the media controls
    kind: actor
    actor: listener
    entities:
      - { entity: player-settings, effect: reads, facts: [Volume] }
    contexts:
      window:
        place: window::player
      bar:
        place: bar-widget::bar-button
      media:
        place: media-controls
  - text: The Product sets the player to the new volume, in steps of 5 for keys and the wheel, between 0 and 100
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Current station] }
    contexts:
      window:
        place: window::player
      bar:
        place: bar-widget::bar-button
      media:
        place: media-controls
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
      media:
        place: media-controls
references:
  - kind: code
    role: implementation
    target: radio-player#set_volume
---

# Set the volume

## Trigger

The station is too loud or too quiet.

## Outcome

Radio plays at the new volume, the slider and the bar's tooltip show it, and the next session starts at it. The desktop's own volume is untouched.

## Edge cases

- Quick changes are combined, so only the latest level is applied once the earlier one finishes.
