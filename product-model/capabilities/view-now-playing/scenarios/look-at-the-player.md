---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener looks at the player in the window
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Current station, Track title, Station logo, Queue, Failure] }
      - { entity: station, effect: reads, facts: [Name] }
    contexts:
      window:
        place: window::player
  - text: The Product shows the station name and logo, the track as title and artist, and Live or Paused with the number of stations queued, or the failure with "Play to retry, or Next."
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Current station, Track title, Queue, Failure] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#playerStatus
---

# Look at the player

## Trigger

The Listener wants to know what is on.

## Outcome

The player names the station and track and says Live or Paused, or shows the failure. After a stop from the media controls it says "Stopped"; with no session it says "Nothing playing" and "Choose a signal to begin".
