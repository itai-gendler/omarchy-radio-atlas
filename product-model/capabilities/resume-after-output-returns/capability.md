---
availability:
  - place: media-controls
domain: playback
references:
  - kind: code
    role: implementation
    target: radio-mpris#Controls.check_return
  - kind: code
    role: implementation
    target: radio-mpris#Controls.resume
---

# Resume after output returns

When the selected output that disappeared during playback comes back, resume the station once on its own.
