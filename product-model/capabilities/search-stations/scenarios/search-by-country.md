---
kind: alternate
routes:
  window: Radio Atlas window
steps:
  - text: The Listener types a country name, a two-letter country code, or an alias such as USA or UK
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: The Product recognizes the country and lists catalog stations with its country code, along with stations whose name or tags contain the text
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Country code, Name, Tags] }
    contexts:
      window:
        place: window::atlas
  - text: The Product asks Radio Browser for that country's stations by code, alongside the name and tag searches
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Country code, Name, Tags, Click count] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: assets/country-search.json
---

# Search by country

## Trigger

The Listener searches for a country rather than a station.

## Outcome

The list holds that country's stations together with stations whose name or tags match, so "UK" finds British stations as well as any named "UK". Text that is not a recognized country matches country names that contain it.
