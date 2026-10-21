---
type: desktop-app
actors:
  - listener
entryPoints:
  - bar-widget: Left click on the Radio Atlas bar button
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml
  - kind: code
    role: implementation
    target: manifest.json
---

# Radio Atlas window

The floating Radio Atlas window that opens over the desktop: the globe, the station lists, the player and the controls page. It is the plugin's panel, opened and closed from the bar.
