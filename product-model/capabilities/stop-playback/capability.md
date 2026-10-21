---
availability:
  - place: window
  - place: bar-widget
  - place: media-controls
  - place: player-command
domain: playback
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#stopPlayer
  - kind: code
    role: implementation
    target: radio-player#stop_player
  - kind: code
    role: implementation
    target: radio-mpris#Controls.stop
---

# Stop playback

Stop the radio, cancelling any random tuning or station that is still starting.
