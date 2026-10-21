---
kind: alternate
routes:
  window: Radio Atlas window
steps:
  - text: The Listener plays another station while a player session is running
    kind: actor
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name] }
      - { entity: player-session, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
  - text: The Product gives the running player the new queue and starts the chosen station unpaused, keeping the volume, mute and output
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: changes, from: Playing, to: Playing, facts: [Current station, Queue, Stream loaded] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: radio-player#play_station
---

# Switch stations while playing

## Trigger

Something is already playing and the Listener starts a different station.

## Outcome

The same player session plays the new station with the new list as its queue; a paused, failed or stopped session starts playing again.
