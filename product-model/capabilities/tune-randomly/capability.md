---
availability:
  - place: window
  - place: bar-widget
references:
  - kind: code
    role: implementation
    target: RadioAtlas.qml#tuneRandom
  - kind: code
    role: implementation
    target: RadioAtlas.qml#randomExclusions
  - kind: code
    role: implementation
    target: radio-fetch#store_random_results
---

# Tune randomly

Play a random working station from Radio Browser that the Listener has not heard recently, with the rest of the random pick as the queue.
