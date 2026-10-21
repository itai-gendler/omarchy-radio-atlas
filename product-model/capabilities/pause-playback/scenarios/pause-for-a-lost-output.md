---
kind: alternate
routes:
  media: Media controls
steps:
  - text: The output radio is playing on disappears and WirePlumber pauses Radio Atlas through the media controls
    kind: actor
    actor: wireplumber
    entities:
      - { entity: player-session, effect: reads, facts: [Current station] }
      - { entity: player-settings, effect: reads, facts: [Selected output] }
    contexts:
      media:
        place: media-controls
  - text: The Product pauses the current station and, when a specific output was selected rather than System default, remembers it as the lost output
    kind: product
    actor: wireplumber
    entities:
      - { entity: player-session, effect: changes, from: Playing, to: Paused, facts: [Lost output] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      media:
        place: media-controls
references:
  - kind: code
    role: implementation
    target: radio-mpris#Controls.pause
  - kind: code
    role: implementation
    target: radio-mpris#policy_sender
---

# Pause for a lost output

## Trigger

Headphones are unplugged, or a Bluetooth or AirPlay speaker drops away, while radio plays on it.

## Outcome

Playback is paused and Radio Atlas waits for the same output to come back. With System default selected, nothing is awaited and the Listener resumes by hand.
