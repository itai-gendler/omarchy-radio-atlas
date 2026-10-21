---
kind: alternate
routes:
  window: Radio Atlas window
steps:
  - text: The player session moves to a station that publishes no location
    kind: condition
    unattended: true
    entities:
      - { entity: player-session, effect: reads, facts: [Current station] }
      - { entity: station, effect: reads, facts: [Location] }
    contexts:
      window:
        place: window::atlas
  - text: The Product turns the globe to the centre of the station's country and highlights it
    kind: product
    entities:
      - { entity: station, effect: reads, facts: [Country, Country code] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: RadioModel.js#countryCentre
---

# Turn to the country centre

## Trigger

The new station has no published coordinates.

## Outcome

The globe faces the station's country as a whole, with the country highlighted.
