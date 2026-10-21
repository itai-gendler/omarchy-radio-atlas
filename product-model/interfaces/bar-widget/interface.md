---
type: desktop-app
actors:
  - listener
references:
  - kind: code
    role: implementation
    target: BarWidget.qml
  - kind: code
    role: implementation
    target: manifest.json
---

# Bar widget

The Radio Atlas button on the Omarchy bar. Left click opens or closes the window, middle click tunes randomly, right click stops playback or resumes the last station, and the mouse wheel changes the radio volume.
