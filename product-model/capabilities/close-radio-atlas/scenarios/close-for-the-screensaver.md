---
kind: alternate
routes:
  window: From the window
steps:
  - text: Omarchy starts its screensaver while the window is open
    kind: condition
    unattended: true
    entities: []
    contexts:
      window:
        place: window
  - text: The Product closes the window as if dismissed
    kind: product
    entities: []
    contexts:
      window:
        place: window
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#handleHyprlandEvent
---

# Close for the screensaver

## Trigger

The desktop goes idle and Omarchy's screensaver opens.

## Outcome

The window is closed so it does not sit over the screensaver; playback is not affected.
