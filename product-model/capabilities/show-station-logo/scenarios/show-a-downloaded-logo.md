---
kind: primary
routes:
  window: Radio Atlas window
  media: Media controls
steps:
  - text: A station that publishes a logo becomes current
    kind: condition
    unattended: true
    entities:
      - { entity: player-session, effect: reads, facts: [Current station] }
      - { entity: station, effect: reads, facts: [Logo address] }
    contexts:
      window:
        place: window::player
      media:
        place: media-controls
  - text: The Product downloads the logo the first time its address is seen and keeps it only if it is an image of at most 1 MiB
    kind: product
    entities:
      - { entity: station, effect: reads, facts: [Logo address] }
    contexts:
      window:
        place: window::player
      media:
        place: media-controls
  - text: The Product shows the stored logo beside the station name in the player and as the artwork in the media controls
    kind: product
    entities:
      - { entity: player-session, effect: changes, facts: [Station logo] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
      media:
        place: media-controls
references:
  - kind: code
    role: implementation
    target: radio-favicon#fetch
---

# Show a downloaded logo

## Trigger

Playback moves to a station with a logo address.

## Outcome

The player and the desktop's media controls show the station's logo; a station played again uses the logo already stored, without downloading it again.
