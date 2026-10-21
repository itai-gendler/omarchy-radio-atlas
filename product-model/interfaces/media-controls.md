---
type: api
actors:
  - listener
  - wireplumber
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: code
    role: implementation
    target: radio-mpris
---

# Media controls

The desktop media-player connection (MPRIS) through which `omarchy.media`, media keys and other desktop controls play, pause, stop, skip and set the volume of Radio Atlas, and see what it is playing. They act only on the player session that is running: opening an address through them is refused with "Select a station in Radio Atlas". WirePlumber uses the same connection to pause playback when an output disappears.
