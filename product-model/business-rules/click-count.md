---
appliesTo:
  - type: capability
    id: play-station
  - type: capability
    id: tune-randomly
  - type: capability-scenario
    id: resume-the-last-station
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: code
    role: implementation
    target: radio-player#play_station
---

# Starting a station counts a click at Radio Browser

Each time a station is started from a list, by random tuning or by resuming the last station, Radio Atlas tells Radio Browser, which keeps the click counts the world and country lists are ordered by. Next, Previous, retrying and resuming a paused station do not count.
