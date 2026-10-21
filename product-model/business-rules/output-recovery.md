---
appliesTo:
  - type: capability
    id: resume-after-output-returns
  - type: capability-scenario
    id: pause-for-a-lost-output
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: code
    role: implementation
    target: radio-mpris#Controls
---

# Playback resumes once when a lost output returns

Only WirePlumber's pause for a disappeared output is awaited, only when a specific output is selected, and only while the station was playing. The same output's return resumes playback once. Any pause, play, stop, station or output change, stream failure or end of the session in between cancels it, and System default never waits, because it does not name the output that left.
