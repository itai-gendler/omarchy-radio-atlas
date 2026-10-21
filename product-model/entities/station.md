---
domain: stations
relations:
  - entity: favorite
    verb: saved as
    cardinality: one-to-one
  - entity: recent-station
    verb: remembered as
    cardinality: one-to-one
references:
  - kind: doc
    role: context
    target: https://www.radio-browser.info/
  - kind: code
    role: implementation
    target: radio-fetch
  - kind: code
    role: implementation
    target: RadioModel.js#mergeGeoStations
---

# Station

A live radio station listed in the Radio Browser directory. Radio Atlas keeps the stations it has fetched as the session's catalog and in its world and country caches, and only lists stations with a web stream address.

## Information kept

- **Name** — the station's name as the directory lists it, or "Unknown station" when it has none
- **Country** — the country name the directory gives
- **Country code** — the two-letter code that places the station in a country
- **Region** — the state or region within the country
- **Language** — the broadcast language
- **Tags** — the genres and keywords the directory lists; a station row shows the first two
- **Codec** — the audio format, such as MP3 or AAC
- **Bitrate** — the stream bitrate in kbps
- **Stream address** — the web address of the station's stream or playlist
- **Logo address** — where the station publishes its logo image
- **Location** — the station's published coordinates, or an estimated point inside its country
- **Approximate location** — whether the location was estimated from the country
- **Click count** — how often the directory has seen the station started; the world and country lists put the most-started first
