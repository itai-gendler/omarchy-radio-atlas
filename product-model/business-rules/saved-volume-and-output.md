---
appliesTo:
  - type: entity
    id: player-settings
  - type: capability
    id: play-station
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: code
    role: implementation
    target: radio-player#play_station
---

# Every player session starts at the saved volume and output

A new player session takes the saved volume and selected output. Volume changes from the window, the bar or the media controls, and output choices, are saved even when nothing is playing, so they carry over to the next session and survive reinstalling the plugin. Mute is not saved.
