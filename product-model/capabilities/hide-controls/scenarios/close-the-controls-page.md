---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener presses ?, Escape or the "Hide controls" button on the Controls page
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window::controls
  - text: The Product shows the globe, lists and player again as they were
    kind: product
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#toggleControls
---

# Close the controls page

## Trigger

The Listener has found the control they wanted.

## Outcome

The globe, list and player are back unchanged.
