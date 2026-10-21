---
kind: primary
routes:
  window: Radio Atlas window
  media: Media controls
steps:
  - text: The Listener presses "Retry station" or Space in the window, or Play in the media controls, while the station shows its failure
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Current station, Failure] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
      media:
        place: media-controls
  - text: The Product opens the same station's stream again and clears the failure
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: changes, from: Failed, to: Playing, facts: [Failure, Stream loaded] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::player
      media:
        place: media-controls
references:
  - kind: code
    role: implementation
    target: radio-status.lua#toggle_playback
---

# Retry the failed station

## Trigger

The Listener thinks the station's trouble was momentary.

## Outcome

The station plays again if its stream answers; if not, it fails again and stays selected. A station whose server repeats an opening clip may play that clip again.
