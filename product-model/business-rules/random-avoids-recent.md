---
appliesTo:
  - type: capability
    id: tune-randomly
    contexts:
      - place: window
      - place: bar-widget
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#randomExclusions
  - kind: code
    role: implementation
    target: radio-fetch#store_random_results
---

# Random tuning avoids what was heard recently

A random pick leaves out the playing station, the previous random pick and the stations in the listening history, and only offers stations that can be placed on the globe. When nothing else is left, it picks from all the stations returned.
