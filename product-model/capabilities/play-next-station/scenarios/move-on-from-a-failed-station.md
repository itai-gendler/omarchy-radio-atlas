---
kind: alternate
routes:
  window: Radio Atlas window
  media: Media controls
steps:
  - text: The Listener presses Next while the current station shows its failure, or after playback was stopped from the media controls
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Current station, Failure] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
      media:
        place: media-controls
  - text: The Product starts the station after the failed or stopped one, unpaused
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: changes, from: Failed, to: Playing, facts: [Current station, Failure, Track title, Stream loaded] }
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

# Move on from a failed station

## Trigger

The failed station is not coming back and the Listener moves on.

## Outcome

The neighbouring station plays with the same queue, so Previous goes back to the failed station.
