---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The window is open and the catalog holds stations but fewer than 5,000
    kind: condition
    unattended: true
    entities:
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
  - text: The Product asks Radio Browser for 500 random working stations
    kind: product
    entities:
      - { entity: station, effect: reads, facts: [Stream address] }
    contexts:
      window:
        place: window::atlas
  - text: The Product adds those the catalog lacks, up to 5,000, to the globe and to the World list when it is showing
    kind: product
    entities:
      - { entity: station, effect: reads, facts: [Name, Location, Approximate location] }
    contexts:
      window:
        place: window::atlas
  - text: The Product asks again a moment later
    kind: product
    entities: []
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#worldExpandProcess
---

# Add stations in the background

## Trigger

The window has been open for a moment with the world stations loaded.

## Outcome

The signal count grows while the window stays open, and the World list keeps its selected station as rows are added.
