---
kind: primary
routes:
  window: Radio Atlas window
  bar: From the bar
  command: Radio player command
steps:
  - text: The Listener presses Stop in the window, right-clicks the bar button while radio plays, or runs radio-player stop
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Current station] }
    contexts:
      window:
        place: window::player
      bar:
        place: bar-widget::bar-button
      command:
        place: player-command
  - text: The Product cancels any random tuning or station still starting, and ends the player session
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: removes, from: Playing }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
      bar:
        place: bar-widget::bar-button
      command:
        place: player-command
  - text: The Product shows "Nothing playing" in the window and turns off the bar button's light
    kind: product
    actor: listener
    entities: []
    contexts:
      window:
        place: window::player
      bar:
        place: bar-widget::bar-button
      command:
        place: player-command
references:
  - kind: code
    role: implementation
    target: radio-player#stop_player
  - kind: code
    role: implementation
    target: BarWidget.qml
---

# Stop the player

## Trigger

The Listener is done listening, or is about to remove the plugin.

## Outcome

No radio plays and the queue is gone. The volume and output stay saved, and the bar can resume the last station later.

## Edge cases

- A paused, failed or stopped session ends the same way.
- Requests made after Stop work as usual; only those already waiting when Stop was pressed are cancelled.
