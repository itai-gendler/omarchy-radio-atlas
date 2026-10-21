---
kind: edge
routes:
  window: Radio Atlas window
steps:
  - text: Three attempts in a row add no station, because the stations returned were already known or the request failed
    kind: condition
    unattended: true
    entities:
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
  - text: The Product stops asking until the window is opened again
    kind: product
    entities: []
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#scheduleWorldExpansion
---

# Stop when nothing new arrives

## Trigger

Radio Browser keeps returning stations the catalog already has, or cannot be reached.

## Outcome

Expansion rests for the rest of this opening; the next opening allows three more tries. Closing the window also stops it.

## Edge cases

- After a failed or empty attempt the next one waits half a minute; after an attempt whose stations were all known, ten seconds.
