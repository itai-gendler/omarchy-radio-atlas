---
kind: alternate
routes:
  window: Radio Atlas window
steps:
  - text: The Listener plays a station from the Favorites or Recent tab
    kind: actor
    actor: listener
    entities:
      - { entity: favorite, effect: reads, facts: [Saved details] }
      - { entity: recent-station, effect: reads, facts: [Saved details] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
  - text: The Product asks Radio Browser for the current details of every station in that tab, keeping the saved details when it cannot answer
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Stream address, Name] }
    contexts:
      window:
        place: window::atlas
  - text: The Product starts a player session with the whole tab as the queue, from the chosen station
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: creates, to: Playing, facts: [Current station, Queue, Muted, Stream loaded] }
      - { entity: player-settings, effect: reads, facts: [Volume, Selected output] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: radio-player#refresh_saved_stations
---

# Play a saved station

## Trigger

The Listener goes back to a favorite or a recent station.

## Outcome

The station plays from its current stream address where the directory has a newer one, with the favorites or the listening history as the queue. The refreshed details serve this queue only; the saved favorites keep the details they were starred with.
