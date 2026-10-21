---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener chooses the Recent tab
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: The Product lists the recent stations newest first, selects the first, and turns the globe to the playing station's country
    kind: product
    actor: listener
    entities:
      - { entity: recent-station, effect: reads, facts: [Saved details, Order] }
      - { entity: player-session, effect: reads, facts: [Current station] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#showRecent
---

# Open recent

## Trigger

The Listener wants to go back to something heard earlier.

## Outcome

Up to 30 recent stations are listed without asking the directory. With none yet, the list says "No listening history yet."
