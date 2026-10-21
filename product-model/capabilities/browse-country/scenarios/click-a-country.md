---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener clicks a country on the globe, away from any station signal
    kind: actor
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
  - text: The Product lists the catalog's stations in that country at once, highlights the country, puts its name in the search field and moves its stations ahead of the rest on the globe
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name, Country code, Codec, Bitrate, Tags, Location] }
    contexts:
      window:
        place: window::atlas
  - text: The Product loads the country's list, from its cached 25 most-started working stations while the cache is fresh, else the world cache's stations in that country while Radio Browser is asked in the background, else Radio Browser's 25 most-started
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Country code, Click count] }
    contexts:
      window:
        place: window::atlas
  - text: The Product merges them into the list and onto the globe, keeping the selected station selected
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name, Country code, Codec, Bitrate, Tags, Location] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#applyCountryStations
  - kind: code
    role: implementation
    target: RadioModel.js#prioritizeStations
---

# Click a country

## Trigger

The Listener wants to hear what a particular country is playing.

## Outcome

The list shows the country's stations, its name in the search field and the hint line, and its signals stay on the globe ahead of background stations. A country with none says "No working stations found in" the country.

## Edge cases

- Clicking another country while the first is still loading switches to the new one; the first country's answer is ignored.
- When the directory cannot be reached, the stations already listed stay with "Showing cached stations · Radio Browser is unavailable".
