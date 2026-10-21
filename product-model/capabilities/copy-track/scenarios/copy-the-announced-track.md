---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The Listener clicks the track line under the station name
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Track title] }
      - { entity: station, effect: reads, facts: [Name] }
    contexts:
      window:
        place: window::player
  - text: The Product copies the track as "Artist - Title", or the title alone, and confirms with "Copied:" and the text
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Track title] }
    contexts:
      window:
        place: window::player
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#copyTrack
---

# Copy the announced track

## Trigger

The Listener wants to look up or save the song that is on.

## Outcome

The clipboard holds the track text with the station's own name and leading separators removed.

## Edge cases

- The track line, and so copying, is offered only while the stream announces a title other than the station's name.
