---
id: radio-atlas
summary: Explore live radio on a rotatable globe from the Omarchy bar and play stations through Omarchy's media controls.
category: media
tags:
  - radio
  - world
  - globe
  - music
  - mpris
authors:
  - name: Akshar Patel
    url: https://github.com/AksharP5
license: MIT
languages:
  - en
limitations:
  - Station listings come from the community-run Radio Browser directory; the audio itself comes from each station's own stream server.
  - After a stream fails, Radio Atlas never reconnects or switches stations on its own.
  - Playback runs in an independent player that keeps playing after the window closes.
  - Favorites, listening history, volume and the selected audio output are kept only on this computer, and stay there when the plugin is removed.
  - Radio Atlas plays through the desktop's PipeWire outputs; an AirPlay speaker appears only once PipeWire offers it as an output.
references:
  - kind: doc
    role: intent
    target: README.md
  - kind: code
    role: implementation
    target: manifest.json
  - kind: code
    role: implementation
    target: RadioAtlas.qml
---

# Radio Atlas

Radio Atlas is an Omarchy plugin for listening to live radio from around the world. Stations appear as signals on a globe the Listener spins and zooms; clicking a signal plays it, and clicking a country lists that country's stations. Search, random tuning, favorites and listening history sit beside the globe, and playback continues in its own player, controlled from the window, the Omarchy bar and the desktop's media controls.

## Intent

Explore live radio on a rotatable globe from the Omarchy bar. Click a station signal to play it, or click a country to browse its stations. Playback runs in `mpv`, with a dedicated MPRIS bridge so `omarchy.media` provides the usual play, pause, previous, and next controls.
