---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener drags across the globe
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: The Product turns the globe with the pointer, more finely the further it is zoomed in, stopping short of the poles
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
    target: Globe.qml#rotateByPointerDelta
---

# Drag the globe

## Trigger

The Listener wants to look at another part of the world.

## Outcome

The globe faces where it was dragged, with the station signals on its visible side. Pointing at a signal names its station, adding "approximate location" when its position is estimated.
