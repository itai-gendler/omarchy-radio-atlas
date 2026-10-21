---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener presses ? or the "Show controls" button
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: The Product replaces the globe, lists and player with the Controls page, one column in a narrow window and two in a wide one
    kind: product
    actor: listener
    entities: []
    contexts:
      window:
        place: window::controls
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#controlSections
---

# Open the controls page

## Trigger

The Listener wants to know what a key or click does.

## Outcome

The Controls page lists the keyboard keys and the mouse and bar actions, scrolling when the window is short.
