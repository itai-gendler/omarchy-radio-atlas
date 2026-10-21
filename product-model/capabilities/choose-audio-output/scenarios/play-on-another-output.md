---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener presses the speaker button
    kind: actor
    actor: listener
    entities:
      - { entity: player-settings, effect: reads, facts: [Selected output] }
    contexts:
      window:
        place: window::player
  - text: The Product lists System default and every PipeWire output by label, marking the selected one
    kind: product
    actor: listener
    entities:
      - { entity: audio-output, effect: reads, facts: [Label] }
      - { entity: player-settings, effect: reads, facts: [Selected output] }
    contexts:
      window:
        place: window::player
  - text: The Listener picks an output
    kind: actor
    actor: listener
    entities:
      - { entity: audio-output, effect: reads, facts: [Label] }
    contexts:
      window:
        place: window::player
  - text: The Product checks the output is still there, moves the playing station to it at once and saves it as the selected output
    kind: product
    actor: listener
    entities:
      - { entity: player-settings, effect: changes, facts: [Selected output] }
      - { entity: player-session, effect: reads, facts: [Current station] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: radio-player#set_output
---

# Play on another output

## Trigger

The Listener wants radio on different speakers, such as an AirPlay speaker in another room.

## Outcome

Radio plays on the chosen output, the speaker button shows it as "Audio output:" with its label, and later sessions start there. Changing outputs cancels any pending return to a lost output.
