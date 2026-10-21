---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener scrolls down over the globe or presses its "Zoom out" button
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: The Product shrinks the globe, by a third for the button and gradually for the wheel, down to about three quarters of its starting size, and clears any landing mark
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

# Zoom out from the globe

## Trigger

The Listener wants to see the whole globe again.

## Outcome

More of the world is in view. At the farthest zoom, "Zoom out" is unavailable.
