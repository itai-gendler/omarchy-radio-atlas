---
entities:
  - entity: station
    shows: [Name]
  - entity: player-session
    shows: [Current station, Track title, Muted, Failure]
  - entity: player-settings
    shows: [Volume]
references:
  - kind: code
    role: implementation
    target: BarWidget.qml
---

# Bar button

The globe button on the bar, lit while radio plays. Its tooltip says what is playing or paused, the stream problem when there is one, and the volume or "muted"; with no player it offers to open Radio Atlas.
