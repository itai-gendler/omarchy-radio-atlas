---
kind: alternate
routes:
  window: Radio Atlas window
  media: Media controls
  bar: From the bar
steps:
  - text: The Listener presses Play in the window or the media controls, or right-clicks the bar button, after playback was stopped from the media controls
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Current station] }
    contexts:
      window:
        place: window::player
      media:
        place: media-controls
      bar:
        place: bar-widget::bar-button
  - text: The Product starts the stopped station again, keeping its queue
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: changes, from: Stopped, to: Playing, facts: [Stream loaded] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
      media:
        place: media-controls
      bar:
        place: bar-widget::bar-button
references:
  - kind: code
    role: implementation
    target: radio-mpris#Controls.play
---

# Resume a stopped station

## Trigger

The Listener stopped radio with a media key and now wants it back.

## Outcome

The station that was stopped plays again, and Next and Previous still move through the same queue.
