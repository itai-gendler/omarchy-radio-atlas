---
appliesTo:
  - type: capability
    id: play-station
  - type: capability
    id: tune-randomly
  - type: capability
    id: play-next-station
  - type: capability
    id: play-previous-station
references:
  - kind: code
    role: implementation
    target: RadioModel.js#stationWindow
  - kind: code
    role: implementation
    target: radio-player#play_station
---

# A station plays with its list as the queue

Playing a station queues the list it was started from, beginning at that station and wrapping around: up to 500 stations around it from the World, search, country or random list, narrowed further when the stations' details would be too large, or the whole Favorites or Recent tab. Next and Previous move only through that queue.
