---
availability:
  - place: window
  - place: bar-widget
  - place: media-controls
domain: playback
references:
  - kind: code
    role: implementation
    target: radio-player#set_volume
  - kind: code
    role: implementation
    target: RadioAtlas.qml#setPlayerVolume
  - kind: code
    role: implementation
    target: BarWidget.qml#changeVolume
  - kind: code
    role: implementation
    target: radio-mpris#VolumeWriter
---

# Change volume

Set the radio's own volume, independently of the desktop volume, and keep it for later sessions.
