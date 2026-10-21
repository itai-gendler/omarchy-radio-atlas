---
kind: alternate
routes:
  window: Radio Atlas window
steps:
  - text: A station already in the listening history starts playing again
    kind: condition
    unattended: true
    entities:
      - { entity: player-session, effect: reads, facts: [Current station, Stream loaded] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
  - text: The Product moves it to the top of the history with its latest details
    kind: product
    entities:
      - { entity: recent-station, effect: changes, facts: [Saved details, Order] }
      - { entity: station, effect: reads, facts: [Name] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: radio-state#write_state
---

# Move a station to the top

## Trigger

The Listener comes back to a station heard before.

## Outcome

The station appears once in the history, at the top.
