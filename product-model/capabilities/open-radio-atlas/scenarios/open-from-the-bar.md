---
kind: primary
routes:
  bar: From the bar
steps:
  - text: The Listener left-clicks the Radio Atlas button on the bar
    kind: actor
    actor: listener
    entities: []
    contexts:
      bar:
        place: bar-widget::bar-button
  - text: The Product sizes a centered floating window to the focused display, inside the area its bars and panels leave free
    kind: product
    actor: listener
    entities: []
    contexts:
      bar:
        place: window
  - text: The Product loads the saved favorites and listening history
    kind: product
    actor: listener
    entities:
      - { entity: favorite, effect: reads, facts: [Saved details, Order] }
      - { entity: recent-station, effect: reads, facts: [Saved details, Order] }
    contexts:
      bar:
        place: window::atlas
  - text: The Product shows the World list and the globe from the session's catalog, or fetches the world stations when the catalog is still empty
    kind: product
    actor: listener
    entities:
      - { entity: station, effect: reads, facts: [Name, Country code, Location] }
    contexts:
      bar:
        place: window::atlas
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#openWindow
  - kind: code
    role: implementation
    target: RadioAtlas.qml#preferredWindowSize
---

# Open from the bar

## Trigger

The Listener wants to explore stations while the window is closed.

## Outcome

The window is open at the largest preferred size the focused display allows, with the World list and globe ready and the keyboard focused on the stations. A display smaller than the preferred size gets a window that fits it; moving to another display takes effect at the next opening.

## Edge cases

- A catalog kept from earlier in the session shows at once; only an empty catalog waits for the world stations.
