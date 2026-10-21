---
domain: playback
references:
  - kind: code
    role: implementation
    target: radio-player
  - kind: code
    role: implementation
    target: radio-status.lua
  - kind: code
    role: implementation
    target: radio-mpris
---

# Player session

The independent radio player that plays a queue of stations. It starts when a station is played with nothing running, keeps playing after the window closes, and ends when the Listener stops it from the window, the bar or the radio player command. Playing a station after that begins a new session.

## Information kept

- **Current station** — the station in the queue that is playing, paused, failed or stopped
- **Queue** — the stations Next and Previous move through: up to 500 from the list the station was started from, beginning at it and wrapping around
- **Track title** — the title the stream announces, split into artist and title where a dash separates them
- **Stream loaded** — whether the current station's stream has started
- **Muted** — whether the radio is muted; a new session starts unmuted
- **Station logo** — the current station's logo once it has been downloaded and checked
- **Failure** — "Stream disconnected" when a started stream ends, or "Station could not be played" when it never starts, with the reason
- **Lost output** — the selected output whose disappearance made WirePlumber pause playback, awaited for one automatic resume

## States

### Playing

The current station's stream plays; the player shows "Live".

### Paused

The current station is paused and stays current; Play resumes it.

### Failed

The current station's stream disconnected or could not be played. It stays current and nothing plays until the Listener retries it or moves to another station.

### Stopped

Stopped from the desktop's media controls. The player keeps its queue and current station, so Play or the bar resumes the same station.
