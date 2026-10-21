---
entities:
  - entity: station
    shows: [Name, Country, Country code, Codec, Bitrate, Tags, Location, Approximate location]
  - entity: favorite
    shows: [Saved details, Order]
  - entity: recent-station
    shows: [Saved details, Order]
  - entity: player-session
    shows: [Current station]
references:
  - kind: code
    role: implementation
    target: Globe.qml
  - kind: code
    role: implementation
    target: RadioAtlas.qml#emptyStateText
---

# Atlas

The globe and the station list beside it. The globe shows every station signal in the session's catalog and the open list, the countries, the number of signals and a hint line that names the highlighted country or the latest problem. The list has World, Favorites and Recent tabs and also holds search, country and random results; each row shows the station's name, country code, codec, bitrate and first two tags, a star for favorites, and a mark on the station that is playing.
