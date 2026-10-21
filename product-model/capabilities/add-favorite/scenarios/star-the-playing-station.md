---
kind: alternate
routes:
  window: Radio Atlas window
steps:
  - text: The Listener presses the empty star beside the playing station in the player
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Current station] }
      - { entity: station, effect: reads, facts: [Name] }
    contexts:
      window:
        place: window::player
  - text: The Product saves the playing station first in the favorites
    kind: product
    actor: listener
    entities:
      - { entity: favorite, effect: creates, facts: [Saved details, Order] }
      - { entity: station, effect: reads, facts: [Name, Country, Country code, Region, Language, Tags, Codec, Bitrate, Stream address, Logo address, Location] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#playingFavoriteButton
---

# Star the playing station

## Trigger

The Listener likes what is playing, whichever list it came from.

## Outcome

The playing station is a favorite and the player's star is filled.
