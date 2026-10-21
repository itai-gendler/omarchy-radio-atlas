---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener clicks a station's row, or presses Enter on the selected station, with nothing playing
    kind: actor
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name] }
    contexts:
      window:
        place: window::atlas
  - text: The Product turns the globe to the station, or to its country's centre when it has no location, and highlights the country
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Location, Country, Country code] }
    contexts:
      window:
        place: window::atlas
  - text: The Product starts a player session with up to 500 stations of the list around the chosen one as its queue, at the saved volume on the selected output
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: creates, to: Playing, facts: [Current station, Queue, Muted, Stream loaded] }
      - { entity: player-settings, effect: reads, facts: [Volume, Selected output] }
      - { entity: station, effect: reads, facts: [Stream address] }
    contexts:
      window:
        place: window::player
  - text: The Product counts the start at Radio Browser and shows the station as Live with the number of stations queued
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name, Click count] }
      - { entity: player-session, effect: reads, facts: [Current station, Queue] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: radio-player#play_station
---

# Play from the list

## Trigger

The Listener picks a station from the World, search, country or random list.

## Outcome

The station plays in its own player, its row is marked as playing, and Next and Previous move through the stations listed around it.

## Edge cases

- When the station's playlist is an M3U or PLS file, the first stream in it plays.
- A large list is narrowed around the chosen station until the queue fits the size the player accepts.
