---
kind: primary
routes:
  window: Radio Atlas window
  bar: From the bar
steps:
  - text: The current station's stream ends after it had started playing
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
  - text: The Product stops at that station instead of advancing, keeping it current and recording "Stream disconnected" as the failure
    kind: product
    entities:
      - { entity: player-session, effect: changes, from: Playing, to: Failed, facts: [Failure, Stream loaded] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
      bar:
        place: bar-widget::bar-button
  - text: The Product shows "Stream disconnected. Play to retry, or Next." in the player and the failure in the bar's tooltip
    kind: product
    entities:
      - { entity: player-session, effect: reads, facts: [Failure] }
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

# Stream disconnects

## Trigger

A station that was playing drops its stream.

## Outcome

The station stays selected and silent with the failure shown; nothing reconnects or switches until the Listener retries, moves on or stops.
