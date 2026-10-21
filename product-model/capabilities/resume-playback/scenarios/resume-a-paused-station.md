---
kind: primary
routes:
  window: Radio Atlas window
  media: Media controls
steps:
  - text: The Listener presses Play or Space in the window, or Play or Play/Pause in the media controls
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Current station] }
    contexts:
      window:
        place: window::player
      media:
        place: media-controls
  - text: The Product unpauses the current station and shows it as Live
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: changes, from: Paused, to: Playing, facts: [] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
      media:
        place: media-controls
references:
  - kind: code
    role: implementation
    target: radio-status.lua#toggle_playback
---

# Resume a paused station

## Trigger

The Listener is ready to listen again.

## Outcome

The same station plays again with the same queue.
