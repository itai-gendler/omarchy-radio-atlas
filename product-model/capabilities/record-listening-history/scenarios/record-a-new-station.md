---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: A newly started station's stream begins playing
    kind: condition
    unattended: true
    entities:
      - { entity: player-session, effect: reads, facts: [Current station, Stream loaded] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
  - text: The Product saves the station's details at the top of the listening history
    kind: product
    entities:
      - { entity: recent-station, as: newest, effect: creates, facts: [Saved details, Order] }
      - { entity: station, effect: reads, facts: [Name, Country, Country code, Region, Language, Tags, Codec, Bitrate, Stream address, Logo address, Location] }
    contexts:
      window:
        place: window::atlas
  - text: When the history already holds 30 stations, the Product drops the oldest
    kind: product
    entities:
      - { entity: recent-station, as: oldest, effect: removes }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: radio-state#write_state
---

# Record a new station

## Trigger

A station starts playing that is not in the listening history yet.

## Outcome

The station is first on the Recent tab and the newest station for the bar to resume; the history never holds more than 30.
