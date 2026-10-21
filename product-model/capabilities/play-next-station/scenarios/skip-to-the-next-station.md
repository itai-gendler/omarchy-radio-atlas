---
kind: primary
routes:
  window: Radio Atlas window
  media: Media controls
steps:
  - text: The Listener presses Next station in the window, or Next in the media controls
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
  - text: The Product starts the next station in the queue, or the first after the last
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

# Skip to the next station

## Trigger

The Listener wants something else from the same list.

## Outcome

The next station of the list the queue came from plays.

## Edge cases

- Next is unavailable in the window while no player session is running.
