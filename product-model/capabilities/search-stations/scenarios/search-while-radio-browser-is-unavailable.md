---
kind: edge
routes:
  window: Radio Atlas window
steps:
  - text: The Listener types a search
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: The Product lists the matching catalog stations
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name, Country, Country code, Region, Language, Tags, Codec] }
    contexts:
      window:
        place: window::atlas
  - text: Any of the directory's name, country or tag searches fails
    kind: condition
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: The Product keeps the catalog matches and warns "Showing cached stations · Radio Browser is unavailable"
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

# Search while Radio Browser is unavailable

## Trigger

The Listener searches while the directory cannot answer all three searches.

## Outcome

The matches already known stay listed with the warning; the partial directory answers are not shown. With no catalog matches, the list says Radio Browser is unavailable.
