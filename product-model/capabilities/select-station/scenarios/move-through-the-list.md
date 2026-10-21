---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener presses Up or Down
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: The Product selects the station above or below, wrapping around at either end, outlines its row and scrolls it into view
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
    target: RadioAtlas.qml#moveSelection
---

# Move through the list

## Trigger

The Listener steps through stations from the keyboard.

## Outcome

One station is selected and outlined, ready for Enter or F. The selection survives list refreshes while the station remains listed.
