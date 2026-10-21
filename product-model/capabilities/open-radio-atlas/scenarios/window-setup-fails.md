---
kind: edge
routes:
  bar: From the bar
steps:
  - text: The Listener left-clicks the Radio Atlas button on the bar
    kind: actor
    actor: listener
    entities: []
    contexts:
      bar:
        place: bar-widget::bar-button
  - text: Setting up the window with the desktop fails
    kind: condition
    entities: []
    contexts:
      bar:
        place: window
  - text: The Product cancels this opening and records the failure in the shell log
    kind: product
    actor: listener
    entities: []
    contexts:
      bar:
        place: window
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#windowSetupProcess
---

# Window setup fails

## Trigger

The Listener opens Radio Atlas while the desktop refuses the window setup.

## Outcome

No window appears for this opening. Clicking the bar button again tries a fresh opening.
