---
domain: stations
references:
  - kind: code
    role: implementation
    target: radio-state#write_state
  - kind: code
    role: implementation
    target: RadioAtlas.qml#toggleFavorite
---

# Favorite

A station the Listener starred, kept in Radio Atlas's saved state so it survives restarts and reinstalls.

## Information kept

- **Saved details** — the station's details as they were when it was starred: name, country, region, language, tags, codec, bitrate, stream and logo addresses and location
- **Order** — favorites are listed newest first, up to 500
