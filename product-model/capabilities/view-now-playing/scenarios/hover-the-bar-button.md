---
kind: alternate
routes:
  bar: From the bar
steps:
  - text: The Listener points at the bar button
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Track title, Muted, Failure] }
      - { entity: player-settings, effect: reads, facts: [Volume] }
    contexts:
      bar:
        place: bar-widget::bar-button
  - text: The Product's tooltip shows "Playing:", "Radio paused:" or the failure, then the track or station name and the volume or "muted", or "Radio stopped" or "Open Radio Atlas"
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name] }
      - { entity: player-session, effect: reads, facts: [Track title, Muted, Failure] }
      - { entity: player-settings, effect: reads, facts: [Volume] }
    contexts:
      bar:
        place: bar-widget::bar-button
references:
  - kind: code
    role: implementation
    target: BarWidget.qml
---

# Hover the bar button

## Trigger

The Listener checks on the radio without opening the window.

## Outcome

The tooltip summarizes the radio in one line; the button itself is lit only while a station is playing, not paused or stopped.
