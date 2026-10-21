---
kind: alternate
routes:
  window: Radio Atlas window
steps:
  - text: The Listener clicks a station signal on the globe
    kind: actor
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name, Location] }
    contexts:
      window:
        place: window::atlas
  - text: When the signal's station is not in the open list, the Product switches to the World list and selects it there
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name] }
    contexts:
      window:
        place: window::atlas
  - text: The Product starts a player session with the stations of that list around it as the queue
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: creates, to: Playing, facts: [Current station, Queue, Muted, Stream loaded] }
      - { entity: player-settings, effect: reads, facts: [Volume, Selected output] }
      - { entity: station, effect: reads, facts: [Stream address] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#activateMapStation
  - kind: code
    role: implementation
    target: Globe.qml#activateAt
---

# Click a signal

## Trigger

The Listener spots a signal on the globe and wants to hear it.

## Outcome

The signal's station plays with the list it belongs to as the queue, whether that is the open list or the World list.
