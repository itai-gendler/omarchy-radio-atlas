---
kind: alternate
routes:
  window: Radio Atlas window
steps:
  - text: The Listener opens the speaker list and picks System default
    kind: actor
    actor: listener
    entities:
      - { entity: player-settings, effect: reads, facts: [Selected output] }
    contexts:
      window:
        place: window::player
  - text: The Product lets the player follow the desktop's current output and saves System default as the selection
    kind: product
    actor: listener
    entities:
      - { entity: player-settings, effect: changes, facts: [Selected output] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: radio-player#set_output
---

# Follow the system default

## Trigger

The Listener wants radio to go wherever the desktop's sound goes.

## Outcome

Radio follows the desktop's output, and the speaker button no longer names a specific output.
