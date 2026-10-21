---
kind: validation
routes:
  bar: From the bar
steps:
  - text: The Listener right-clicks the bar button while no player session is running
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [] }
    contexts:
      bar:
        place: bar-widget::bar-button
  - text: The listening history is empty
    kind: condition
    entities:
      - { entity: recent-station, effect: reads, facts: [] }
    contexts:
      bar:
        place: bar-widget::bar-button
  - text: The Product starts nothing and the bar button stays as it was
    kind: product
    actor: listener
    entities: []
    contexts:
      bar:
        place: bar-widget::bar-button
references:
  - kind: code
    role: implementation
    target: radio-player#resume_last
---

# Nothing to resume

## Trigger

The Listener right-clicks the bar before any station has ever played.

## Outcome

Nothing happens; there is no station to go back to until one has played.
