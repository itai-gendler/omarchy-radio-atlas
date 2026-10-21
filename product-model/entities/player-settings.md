---
singleton: true
domain: playback
references:
  - kind: code
    role: implementation
    target: radio-state#write_volume
  - kind: code
    role: implementation
    target: radio-state#write_output
---

# Player settings

The listening settings Radio Atlas keeps beside favorites and history, applied to every new player session.

## Information kept

- **Volume** — radio volume from 0 to 100; 70 until the Listener changes it
- **Selected output** — the audio output radio plays on, or System default to follow the desktop's current output
