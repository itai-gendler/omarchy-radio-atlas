---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener presses the empty star on a station's row, or F with the station selected
    kind: actor
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name] }
    contexts:
      window:
        place: window::atlas
  - text: The Product saves that one station's details first in the favorites and fills its star
    kind: product
    actor: listener
    entities:
      - { entity: favorite, effect: creates, facts: [Saved details, Order] }
      - { entity: station, effect: reads, facts: [Name, Country, Country code, Region, Language, Tags, Codec, Bitrate, Stream address, Logo address, Location] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: radio-state#write_state
---

# Star a listed station

## Trigger

The Listener wants to keep a station they found.

## Outcome

The station is first on the Favorites tab and its star is filled wherever it is listed. Favorites hold up to 500 stations.
