---
domain: stations
references:
  - kind: code
    role: implementation
    target: radio-state#write_state
  - kind: code
    role: implementation
    target: RadioAtlas.qml#recordPlayed
---

# Recent station

A station in the Listener's listening history: one that started playing. The Recent tab lists them, and the bar resumes the newest.

## Information kept

- **Saved details** — the station's details as they were when it last started playing: name, country, region, language, tags, codec, bitrate, stream and logo addresses and location
- **Order** — newest first; the history holds the 30 most recent stations, each once
