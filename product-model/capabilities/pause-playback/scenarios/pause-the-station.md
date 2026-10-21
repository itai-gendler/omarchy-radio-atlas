---
kind: primary
routes:
  window: Radio Atlas window
  media: Media controls
steps:
  - text: The Listener presses Pause or Space in the window, or Pause or Play/Pause in the desktop's media controls
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Current station] }
    contexts:
      window:
        place: window::player
      media:
        place: media-controls
  - text: The Product pauses the current station and shows "Paused" in the player, the bar and the media controls
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: changes, from: Playing, to: Paused, facts: [] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
      media:
        place: media-controls
references:
  - kind: code
    role: implementation
    target: radio-mpris#Controls.pause
---

# Pause the station

## Trigger

The Listener needs quiet for a moment.

## Outcome

The current station is paused and stays current with its queue. A pause the Listener asks for cancels any pending return to a lost output.
