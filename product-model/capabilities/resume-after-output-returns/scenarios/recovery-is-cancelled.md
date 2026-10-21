---
kind: edge
routes:
  media: Media controls
steps:
  - text: Before the lost output returns, playback is paused again by hand, played, stopped or moved to another station or output, or the stream fails
    kind: condition
    unattended: true
    entities:
      - { entity: player-session, effect: reads, facts: [Lost output] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      media:
        place: media-controls
  - text: The Product forgets the lost output, so its return does not resume playback
    kind: product
    entities:
      - { entity: player-session, effect: changes, facts: [Lost output] }
    contexts:
      media:
        place: media-controls
references:
  - kind: code
    role: implementation
    target: radio-mpris#Controls.cancel
---

# Recovery is cancelled

## Trigger

The Listener or the stream acts first, before the output comes back.

## Outcome

Playback stays as the Listener left it when the output returns. A station that was already paused before the output disappeared stays paused.
