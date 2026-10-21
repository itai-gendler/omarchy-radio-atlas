---
scope: The Radio Atlas plugin's window, globe, bar widget, station directory requests, saved state, player and media-control bridge.
method: Static reading of the tracked plugin files at the pinned commit, with tests read as supporting evidence.
covered:
  - description: Window, globe, station lists and player panel, with their station and map helpers.
    paths: [RadioAtlas.qml, Globe.qml, RadioModel.js]
  - description: Bar widget.
    paths: [BarWidget.qml]
  - description: Station directory requests, world and country caches, and the bundled country search names.
    paths: [radio-fetch, assets/country-search.json]
  - description: Saved favorites, listening history, volume and output.
    paths: [radio-state]
  - description: Player control, queue and status reporting.
    paths: [radio-player, radio-status.lua]
  - description: Media-control bridge and station logo downloads.
    paths: [radio-mpris, radio-favicon]
  - description: Window sizing setup and the plugin manifest.
    paths: [radio-window, manifest.json]
exclusions:
  - description: Tests, fixtures and test runners.
    paths: [tests/]
  - description: Continuous integration and pull-request evidence images.
    paths: [.github/, docs/]
  - description: Shipped map geometry, its attribution, the preview image and the licence.
    paths: [assets/countries.json, assets/NOTICE.md, preview.png, LICENSE]
unmapped:
  - description: Playback network isolation and the stream relay the player connects through.
    paths: [radio-proxy, radio-sandbox, radio-session]
limitations: []
---

# Coverage
