---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The player session's current station changes, from the window, the bar or the media controls
    kind: condition
    unattended: true
    entities:
      - { entity: player-session, effect: reads, facts: [Current station] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
  - text: The Product selects that station in the open list when it is there and marks it as playing
    kind: product
    entities:
      - { entity: station, effect: reads, facts: [Name] }
    contexts:
      window:
        place: window::atlas
  - text: The Product turns the globe to the station's location and highlights its country
    kind: product
    entities:
      - { entity: station, effect: reads, facts: [Location, Country, Country code] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#applyPlayerState
---

# Turn to the new station

## Trigger

Next, Previous, random tuning or a desktop media key moves playback to another station.

## Outcome

The globe faces the station now playing, its country is highlighted and named in the hint line, and its row is selected in the open list. Track-title, volume and pause updates leave the globe and the selection where they are.
