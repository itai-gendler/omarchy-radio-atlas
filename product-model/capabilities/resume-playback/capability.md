---
availability:
  - place: window
  - place: media-controls
  - place: bar-widget
domain: playback
references:
  - kind: code
    role: implementation
    target: radio-mpris#Controls.play
  - kind: code
    role: implementation
    target: radio-player#resume_last
  - kind: code
    role: implementation
    target: BarWidget.qml
---

# Resume playback

Continue the paused or stopped station, or, with nothing playing, start the station heard most recently.
