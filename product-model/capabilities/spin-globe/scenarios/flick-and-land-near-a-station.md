---
kind: alternate
routes:
  window: Radio Atlas window
steps:
  - text: The Listener flicks the globe and lets go
    kind: actor
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: The Product keeps the globe turning in the flick's direction, slowing it steadily and capping how fast it can go
    kind: product
    actor: listener
    entities: []
    contexts:
      window:
        place: window::atlas
  - text: When the globe settles, the Product finds the visible signal nearest the centre of the view, passing over the playing station, or the selected one when nothing plays, while another is in view
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Location] }
      - { entity: player-session, effect: reads, facts: [Current station] }
    contexts:
      window:
        place: window::atlas
  - text: The Product marks that signal with "Landed near" and the station's name, adding "approximate location" when its position is estimated
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name, Approximate location] }
    contexts:
      window:
        place: window::atlas
  - text: The Listener clicks the marked signal to play it, or drags again to clear the mark
    kind: actor
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: Globe.qml#finishKineticRotation
  - kind: code
    role: implementation
    target: RadioModel.js#nearestVisibleStation
---

# Flick and land near a station

## Trigger

The Listener spins the globe to see where it stops, like spinning a real one.

## Outcome

The globe comes to rest with one nearby station named, so a flick is a way of discovering a station somewhere new. The mark stays while the signal is in view and the station remains on the globe, including across station refreshes.

## Edge cases

- A slow release does not coast; the globe stops where it was let go and nothing is marked.
- When the only signal in view is the station passed over, that station is marked.
