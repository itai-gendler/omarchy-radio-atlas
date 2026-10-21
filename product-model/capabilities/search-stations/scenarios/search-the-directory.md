---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener presses / and types into "Search station, country, or genre"
    kind: actor
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
  - text: The Product lists up to 150 catalog stations whose name, country, country code, region, language, tags or codec contain the text
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name, Country, Country code, Region, Language, Tags, Codec] }
    contexts:
      window:
        place: window::atlas
  - text: After a short pause in typing, or on Enter, the Product asks Radio Browser for the most-started working stations matching the text by name, by country and by tag
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name, Country, Tags, Click count] }
    contexts:
      window:
        place: window::atlas
  - text: The Product replaces the list with the directory's matches, keeping the selected station selected when it is among them
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
    target: radio-fetch#fetch_search
---

# Search the directory

## Trigger

The Listener has a station, genre or place in mind.

## Outcome

The list holds the directory's stations matching the text, and their signals join the globe. A search with no matches says "No stations match" with the text.

## Edge cases

- A newer search replaces one still waiting; only the answer to the text in the field is shown.
