---
kind: primary
result: achieved
routes:
  bar: From the bar
steps:
  - text: The Listener middle-clicks the Radio Atlas button on the bar
    kind: actor
    actor: listener
    capability: tune-randomly
    entities: []
    contexts:
      bar:
        place: bar-widget::bar-button
  - text: The Product opens the window and plays a random station not heard recently
    kind: product
    actor: listener
    capability: tune-randomly
    entities:
      - { entity: recent-station, effect: reads, facts: [Saved details] }
      - { entity: player-session, effect: creates, to: Playing, facts: [Current station, Queue, Muted, Stream loaded] }
      - { entity: player-settings, effect: reads, facts: [Volume, Selected output] }
      - { entity: station, effect: reads, facts: [Name] }
    contexts:
      bar:
        place: window::player
  - text: The Listener presses the empty star beside the playing station in the player
    kind: actor
    actor: listener
    capability: add-favorite
    entities:
      - { entity: player-session, effect: reads, facts: [Current station] }
      - { entity: station, effect: reads, facts: [Name] }
    contexts:
      bar:
        place: window::player
  - text: The Product saves the playing station first in the favorites
    kind: product
    actor: listener
    capability: add-favorite
    entities:
      - { entity: favorite, effect: creates, facts: [Saved details, Order] }
      - { entity: station, effect: reads, facts: [Name, Country, Country code, Region, Language, Tags, Codec, Bitrate, Stream address, Logo address, Location] }
    contexts:
      bar:
        place: window::player
---

# Tune from the bar and star it

## Trigger

The Listener wants something new and middle-clicks the bar.

## Outcome

The station found at random is playing and saved at the top of the favorites.
