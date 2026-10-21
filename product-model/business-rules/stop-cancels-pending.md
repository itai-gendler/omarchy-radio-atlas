---
appliesTo:
  - type: capability
    id: stop-playback
  - type: capability
    id: tune-randomly
  - type: capability
    id: play-station
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: code
    role: implementation
    target: radio-player#cancel_pending_plays
---

# Stop cancels what is waiting to start

Stop, from any surface, cancels random tuning and station starts that are still waiting, including before any audio plays, so nothing starts after the Listener stopped. Requests made after the Stop are handled as usual.
