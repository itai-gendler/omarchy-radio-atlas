---
kind: alternate
routes:
  window: Radio Atlas window
steps:
  - text: A country's cache finishes refreshing while that country's list is open
    kind: condition
    unattended: true
    entities:
      - { entity: station, effect: reads, facts: [Country code] }
    contexts:
      window:
        place: window::atlas
  - text: The Product merges the refreshed stations into the open list and onto the globe, keeping the selected station selected
    kind: product
    entities:
      - { entity: station, effect: reads, facts: [Name, Country code, Codec, Bitrate, Tags, Location] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#applyCountryStations
---

# Refreshed country reaches the open list

## Trigger

The Listener is still looking at a country when its background refresh completes.

## Outcome

The country list shows the refreshed stations without losing the selection. A refresh for any other country leaves the open list alone.
