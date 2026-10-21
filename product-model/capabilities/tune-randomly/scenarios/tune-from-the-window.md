---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener presses R or the "Tune randomly" button
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: The Product clears the list and asks Radio Browser for 60 random working stations
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Stream address] }
    contexts:
      window:
        place: window::atlas
  - text: The Product keeps those with a location or a country, drops the playing station, the last random pick and the recent stations, and shuffles the rest
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Location, Country code] }
      - { entity: recent-station, effect: reads, facts: [Saved details] }
      - { entity: player-session, effect: reads, facts: [Current station] }
    contexts:
      window:
        place: window::atlas
  - text: The Product lists the pick and plays its first station, with the pick as the queue
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name, Click count] }
      - { entity: player-session, effect: creates, to: Playing, facts: [Current station, Queue, Muted, Stream loaded] }
      - { entity: player-settings, effect: reads, facts: [Volume, Selected output] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: radio-fetch#store_random_results
---

# Tune from the window

## Trigger

The Listener wants to be surprised.

## Outcome

A station the Listener has not heard recently plays, the random pick fills the list, and Next moves on to another random station.

## Edge cases

- When every station returned was heard recently, the pick is made from all of them instead.
- Pressing R again while a pick is loading asks again once the first answer arrives.
