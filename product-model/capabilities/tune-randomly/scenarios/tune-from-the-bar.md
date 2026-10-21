---
kind: alternate
routes:
  bar: From the bar
steps:
  - text: The Listener middle-clicks the Radio Atlas button on the bar
    kind: actor
    actor: listener
    entities: []
    contexts:
      bar:
        place: bar-widget::bar-button
  - text: The Product opens the window, loading the world stations if the catalog is empty
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name, Location] }
    contexts:
      bar:
        place: window::atlas
  - text: The Product tunes randomly as from the window, skipping recently heard stations, and plays the first station of the pick
    kind: product
    actor: listener
    entities:
      - { entity: recent-station, effect: reads, facts: [Saved details] }
      - { entity: player-session, effect: creates, to: Playing, facts: [Current station, Queue, Muted, Stream loaded] }
      - { entity: player-settings, effect: reads, facts: [Volume, Selected output] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      bar:
        place: window::player
references:
  - kind: code
    role: implementation
    target: BarWidget.qml
  - kind: code
    role: implementation
    target: RadioAtlas.qml#openWindow
---

# Tune from the bar

## Trigger

The Listener wants random radio without opening the window first.

## Outcome

The window is open on the random pick and its first station plays.
