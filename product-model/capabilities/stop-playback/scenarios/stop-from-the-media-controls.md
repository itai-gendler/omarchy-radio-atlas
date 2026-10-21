---
kind: alternate
routes:
  media: Media controls
steps:
  - text: The Listener presses Stop in the desktop's media controls
    kind: actor
    actor: listener
    entities:
      - { entity: player-session, effect: reads, facts: [Current station] }
    contexts:
      media:
        place: media-controls
  - text: The Product cancels any random tuning or saved station still starting, stops the stream and clears any failure, keeping the queue and the current station
    kind: product
    actor: listener
    entities:
      - { entity: player-session, effect: changes, from: Playing, to: Stopped, facts: [Failure, Stream loaded] }
      - { entity: station, effect: reads, facts: [] }
    contexts:
      media:
        place: media-controls
  - text: The Product shows "Stopped" in the window and "Radio stopped" on the bar, with the bar button's light off
    kind: product
    actor: listener
    entities: []
    contexts:
      media:
        place: media-controls
references:
  - kind: code
    role: implementation
    target: radio-mpris#Controls.stop
---

# Stop from the media controls

## Trigger

The Listener stops radio with a media key or the desktop's media controls.

## Outcome

Nothing plays, but the session is kept: Play, the bar's right-click or Next picks up from the stopped station and its queue.

## Edge cases

- Stopping from the media controls while already stopped still cancels anything waiting to start.
