---
kind: alternate
routes:
  window: Radio Atlas window
  bar: From the bar
steps:
  - text: The current station's stream never starts, or its playlist turns out to be empty
    kind: condition
    unattended: true
    entities:
      - { entity: player-session, effect: reads, facts: [Current station, Stream loaded] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
      bar:
        place: bar-widget::bar-button
  - text: The Product keeps the station current and records "Station could not be played" as the failure, with the reason
    kind: product
    entities:
      - { entity: player-session, effect: changes, from: Playing, to: Failed, facts: [Failure] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
      bar:
        place: bar-widget::bar-button
references:
  - kind: code
    role: implementation
    target: radio-status.lua
---

# Station cannot be played

## Trigger

A station is started whose stream does not answer, or whose playlist lists no streams.

## Outcome

The station stays selected with "Station could not be played. Play to retry, or Next." and Radio Atlas does not try the next station on its own.
