---
kind: primary
routes:
  window: Radio Atlas window
  media: Media controls
steps:
  - text: The Listener presses Previous station in the window, or Previous in the media controls
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Queue] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
      media:
        place: media-controls
  - text: The Product starts the previous station in the queue, or the last when the first was playing
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: changes, from: Playing, to: Playing, facts: [Current station, Track title, Stream loaded] }
      - { entity: station, effect: reads, facts: [Name, Stream address] }
    contexts:
      window:
        place: window::player
      media:
        place: media-controls
references:
  - kind: code
    role: implementation
    target: radio-status.lua#navigate
---

# Go back a station

## Trigger

The Listener wants the station before.

## Outcome

The previous station of the list the queue came from plays.

## Edge cases

- From a failed or stopped station, Previous plays its neighbour just as Next does.
