---
entities:
  - entity: station
    shows: [Name]
  - entity: player-session
    shows: [Current station, Queue, Track title, Muted, Station logo, Failure]
  - entity: player-settings
    shows: [Volume, Selected output]
    collects: [Volume, Selected output]
  - entity: audio-output
    shows: [Label]
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml
---

# Player

The player below the station list: the current station's name and logo, the track it announces, the playing status with the number of stations queued, a star for the playing station, Previous, Play or Pause, Next and Stop, mute, the volume slider, and the speaker button that opens the audio output list.
