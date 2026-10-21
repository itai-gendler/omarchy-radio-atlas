---
kind: edge
routes:
  window: Radio Atlas window
  media: Media controls
steps:
  - text: The current station has no logo address, or its logo cannot be downloaded or is not an acceptable image
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
  - text: The Product shows the station name without a logo and offers no artwork to the media controls
    kind: product
    entities:
      - { entity: player-session, effect: reads, facts: [Station logo] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
      media:
        place: media-controls
references:
  - kind: code
    role: implementation
    target: radio-mpris#Artwork.finished
---

# No usable logo

## Trigger

The current station's logo is missing or refused.

## Outcome

The player keeps its text-only layout and the media controls show no artwork; playback and the controls are unaffected.
