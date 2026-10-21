---
kind: primary
routes:
  window: From the window
  bar: From the bar
steps:
  - text: The Listener presses the close button or Escape in the window, or left-clicks the bar button while the window is open
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window
      bar:
        place: bar-widget::bar-button
  - text: The Product hides the window and stops growing the catalog in the background, while the player session plays on
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Current station] }
    contexts:
      window:
        place: window
      bar:
        place: window
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#close
  - kind: code
    role: implementation
    target: BarWidget.qml
---

# Close the window

## Trigger

The Listener is done browsing for now.

## Outcome

The window is gone and any station that was playing carries on; the bar and media controls still control it.

## Edge cases

- Escape first closes the output list, leaves the search field (clearing it when it holds text) or hides the controls page; it closes the window only when none of those applies.
