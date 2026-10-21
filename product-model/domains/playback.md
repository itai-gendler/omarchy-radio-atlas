---
references:
  - kind: code
    role: implementation
    target: radio-player
---

# Playback

What happens to the station that is playing: pausing, resuming, retrying, moving through the queue, stopping, mute, volume and the audio output.

## Boundary

It does not own starting a station, which the globe, the lists and the bar all reach, or the listening history kept as stations play.
