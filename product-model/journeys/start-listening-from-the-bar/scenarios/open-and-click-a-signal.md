---
kind: primary
result: achieved
routes:
  bar: From the bar
steps:
  - text: The Listener left-clicks the Radio Atlas button on the bar
    kind: actor
    actor: listener
    capability: open-radio-atlas
    entities: []
    contexts:
      bar:
        place: bar-widget::bar-button
  - text: The Product opens the window on the World list and the globe
    kind: product
    actor: listener
    capability: open-radio-atlas
    entities:
      - { entity: station, effect: reads, facts: [Name, Location] }
    contexts:
      bar:
        place: window::atlas
  - text: The Listener clicks a station signal on the globe
    kind: actor
    actor: listener
    capability: play-station
    entities:
      - { entity: station, effect: reads, facts: [Name, Location] }
    contexts:
      bar:
        place: window::atlas
  - text: The Product starts a player session on that station with the World list as its queue
    kind: product
    actor: listener
    capability: play-station
    entities:
      - { entity: player-session, effect: creates, to: Playing, facts: [Current station, Queue, Muted, Stream loaded] }
      - { entity: player-settings, effect: reads, facts: [Volume, Selected output] }
      - { entity: station, effect: reads, facts: [Stream address] }
    contexts:
      bar:
        place: window::player
---

# Open and click a signal

## Trigger

The Listener wants radio and starts from the bar.

## Outcome

The chosen station plays, the globe faces it, and the bar button is lit.
