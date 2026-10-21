---
kind: edge
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
  - text: PipeWire's outputs cannot be listed
    kind: condition
    entities: []
    contexts:
      window:
        place: window::player
  - text: The Product offers only System default and says "Audio outputs are unavailable"
    kind: product
    actor: listener
    entities:
      - { entity: audio-output, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#outputsProcess
---

# Outputs unavailable

## Trigger

The Listener opens the output list while PipeWire does not answer.

## Outcome

System default can still be chosen; specific outputs cannot. Picking an output that has disappeared since the list was shown says "Could not change audio output" and keeps the selection.
