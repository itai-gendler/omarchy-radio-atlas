---
kind: primary
routes:
  window: Radio Atlas window
steps:
  - text: The world or country list was shown from a cache more than a day old
    kind: condition
    unattended: true
    entities:
      - { entity: station, effect: reads, facts: [] }
    contexts:
      window:
        place: window::atlas
  - text: The Product fetches the same list again from Radio Browser in the background, retrying once and trying each directory server in turn
    kind: product
    entities:
      - { entity: station, effect: reads, facts: [Click count] }
    contexts:
      window:
        place: window::atlas
  - text: The Product replaces the cache with the fresh stations for the next time the list is shown
    kind: product
    entities:
      - { entity: station, effect: changes, facts: [Name, Country, Region, Language, Tags, Codec, Bitrate, Stream address, Logo address, Location, Click count] }
    contexts:
      window:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: radio-fetch#request
---

# Refresh a stale cache

## Trigger

A world or country list was served from a cache older than a day.

## Outcome

The cache holds the directory's current stations, ready for the next world or country list; the list already shown is not held up.

## Edge cases

- A failed refresh leaves the old cache in place, and the next time the list is shown tries again.
