---
kind: alternate
routes:
  media: Media controls
steps:
  - text: The Listener opens the desktop's media controls while a player session runs
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Track title, Station logo] }
    contexts:
      media:
        place: media-controls
  - text: The Product presents itself as Radio Atlas with the announced title, the station logo and Playing, Paused or Stopped
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Track title, Station logo] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      media:
        place: media-controls
references:
  - kind: code
    role: implementation
    target: radio-mpris#player_properties
---

# See it in the media controls

## Trigger

The Listener uses `omarchy.media` or another desktop media widget.

## Outcome

Radio Atlas appears as a media player with the current title and logo. A failed station shows as Stopped there, without a title, until it is retried or the Listener moves on.
