---
kind: edge
routes:
  window: Radio Atlas window
steps:
  - text: The Listener chooses the World tab
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: Radio Browser does not answer with valid world stations
    kind: condition
    entities:
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
  - text: The Product keeps the cached stations listed and warns "Showing cached stations · Radio Browser is unavailable", or says "Radio Browser is unavailable. Try again shortly." when nothing is cached
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
    target: RadioAtlas.qml#fetchProcess
---

# Radio Browser unavailable

## Trigger

The World list is opened while the directory cannot be reached.

## Outcome

Whatever was already known stays listed, with the warning on the globe's hint line; with nothing known, the list itself explains the directory is unavailable.
