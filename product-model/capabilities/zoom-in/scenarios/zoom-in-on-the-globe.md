---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener scrolls up over the globe or presses its "Zoom in" button
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: The Product enlarges the globe, by half again for the button and gradually for the wheel, up to 24 times its starting size, and clears any landing mark
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Location] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: Globe.qml#zoomBy
---

# Zoom in on the globe

## Trigger

Signals are too close together to pick one.

## Outcome

The globe is larger and nearby signals spread apart. At the closest zoom, "Zoom in" is unavailable.
