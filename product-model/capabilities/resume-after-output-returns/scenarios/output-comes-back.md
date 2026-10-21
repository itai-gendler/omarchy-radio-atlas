---
kind: primary
routes:
  media: Media controls
steps:
  - text: The lost output reappears among PipeWire's outputs while the station is still paused for it
    kind: condition
    unattended: true
    entities:
      - { entity: player-session, effect: reads, facts: [Lost output] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      media:
        place: media-controls
  - text: The Product waits a moment, checks the same output is still selected and the station still paused, and resumes playback once
    kind: product
    entities:
      - { entity: player-session, effect: changes, from: Paused, to: Playing, facts: [Lost output] }
      - { entity: player-settings, effect: reads, facts: [Selected output] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      media:
        place: media-controls
references:
  - kind: code
    role: implementation
    target: radio-mpris#Controls.resume
---

# Output comes back

## Trigger

The headphones or speaker that dropped out are back.

## Outcome

The station plays again on the same output without the Listener pressing Play, and nothing more is awaited.
