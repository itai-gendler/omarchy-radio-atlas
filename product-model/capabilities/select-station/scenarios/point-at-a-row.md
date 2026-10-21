---
kind: alternate
routes:
  window: Radio Atlas window
steps:
  - text: The Listener moves the pointer over a row of the list
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: The Product selects that station and drops the keyboard outline
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#stationList
---

# Point at a row

## Trigger

The Listener uses the mouse instead of the keyboard.

## Outcome

The station under the pointer is the selected one; scrolling the list without moving the pointer does not change it.
