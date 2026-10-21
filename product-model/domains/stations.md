---
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml
  - kind: code
    role: implementation
    target: radio-fetch
---

# Stations

Finding stations: the World, Favorites and Recent lists, search, selecting a station, the session's catalog and the caches behind them.

## Boundary

It does not own starting a station, which the globe also reaches, pausing or stopping it, which belong to Playback, starring a station, which every list and the player reach, or random tuning, which the bar also reaches.
