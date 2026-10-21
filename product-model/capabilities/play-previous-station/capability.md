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
    target: radio-mpris#Previous
---

# Play previous station

Move playback to the previous station in the queue, wrapping around at its start.
