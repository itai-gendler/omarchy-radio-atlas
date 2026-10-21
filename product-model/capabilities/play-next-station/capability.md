---
availability:
  - place: window
  - place: media-controls
domain: playback
references:
  - kind: code
    role: implementation
    target: radio-status.lua#navigate
  - kind: code
    role: implementation
    target: radio-mpris#Next
---

# Play next station

Move playback to the next station in the queue, wrapping around at its end.
