---
kind: alternate
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
  - text: The listening history holds at least one station
    kind: condition
    entities:
      - { entity: recent-station, effect: reads, facts: [Order] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      bar:
        place: bar-widget::bar-button
  - text: The Product asks Radio Browser for the current details of every recent station, keeping the saved details when it cannot answer
    kind: product
    actor: listener
    entities:
      - { entity: recent-station, effect: reads, facts: [Saved details] }
      - { entity: station, effect: reads, facts: [Stream address, Name] }
    contexts:
      bar:
        place: bar-widget::bar-button
  - text: The Product starts a player session on the newest recent station, with the whole history as the queue, at the saved volume on the selected output
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: creates, to: Playing, facts: [Current station, Queue, Muted, Stream loaded] }
      - { entity: player-settings, effect: reads, facts: [Volume, Selected output] }
      - { entity: recent-station, effect: reads, facts: [Order] }
    contexts:
      bar:
        place: bar-widget::bar-button
  - text: The Product counts the start at Radio Browser and lights the bar button once the station plays
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Click count] }
    contexts:
      bar:
        place: bar-widget::bar-button
references:
  - kind: code
    role: implementation
    target: radio-player#resume_last
  - kind: code
    role: implementation
    target: radio-player#refresh_saved_stations
---

# Resume the last station

## Trigger

The Listener wants radio back from the bar without opening the window.

## Outcome

The station heard most recently plays from its current stream address, and Next and Previous move through the listening history.

## Edge cases

- Right-clicking again before the station has started stops the request instead.
