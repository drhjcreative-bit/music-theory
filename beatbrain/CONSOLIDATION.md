# BEAT BRAIN — consolidation map

BEAT BRAIN is the flagship studio unit. This document records what was absorbed
from each music app, what was cut, and what stays a sister app.

Run it: open `beatbrain/index.html` in any modern browser. No build step, no
server, no accounts — everything runs and persists on-device (IndexedDB +
localStorage).

## Where each module came from

| BEAT BRAIN module | Absorbed from | What it keeps |
|---|---|---|
| LIBRARY | sound.WAV (wavPRO) Songs/Library | drag-drop import, waveform render, automatic BPM + key analysis, on-device persistence across reloads |
| GRID | Mimic Media Maker Sequencer/Grid | 8-voice × 16-step sequencer with a synthesized kit, swing, tempo sync to the loaded track, pattern inference from the track, beat-MIDI export |
| KEYS | sound.WAV Interpolator + Notes | key/mode detection (Krumhansl–Schmuckler), scale notes with degrees, diatonic chords, named progressions — all auditionable, progression-MIDI export |
| LAYERS | sound.WAV Layers + Mimic Stems | 7-band frequency isolation (Sub → Air) on the live player with per-band gain/mute/solo, offline bounce of the current layer mix to WAV |
| VIZ | Mimic Visualizer | spectrum / scope / orb modes driven by the master bus, clip recording (canvas + audio → webm) |
| BRAIN | sound.WAV Brain/Brain Feed | tagged production notes and references, signature readout synthesized from the feed plus library analysis |
| EXPORT | Mimic Export | one hub for every bounce this session: MIDI, WAV layer mixes, viz clips, with in-app audio preview |
| Transport deck | both | persistent player with waveform scrubber and live BPM/KEY LED readout |

## Shaved fat

Cut deliberately — these diluted the studio tool:

- **Accounts, pricing pages, community/discover feeds** (Sound Wave) — a studio
  unit is not a SaaS funnel.
- **Playlists and album sequencing** (sound.WAV) — listening-library features,
  not production features.
- **Takes editor** (sound.WAV) — overlapped with GRID + LAYERS for the actual
  workflow it served.
- **Video meeting client** (Halo, inside Hookcutter) — unrelated to music.
- **ML stem separation** (Mimic) — the one real feature that cannot run in a
  self-contained client. LAYERS' honest 7-band DSP covers most day-to-day use;
  if true stem separation returns, it should be a small server endpoint feeding
  BEAT BRAIN, not a separate app.

## The suite

- **BEAT BRAIN** (this app) — the flagship studio: analyze, sequence, harmonize,
  isolate, visualize, export.
- **Hookcutter** — stays a sister app. It is a video/clipping pipeline
  (Whisper, scene detection, ffmpeg rendering); bolting it into a browser studio
  would flatter neither. Its beat-sync already speaks the same language as
  BEAT BRAIN's BPM analysis.
- **Sound Wave** — its distinct idea (AI mix *guidance* + community) is a
  finishing service, not a studio surface. Fold its guidance into BEAT BRAIN
  later as a server-backed panel, or keep it as the "finishing" sister app.
  Its remaining features are already covered here.
- **sound.WAV / Mimic Media Maker** — absorbed; retire once BEAT BRAIN covers
  daily use.

## Design language

Hardware instrument, not web app: asphalt faceplate, silkscreen labels
(Chakra Petch / IBM Plex Mono), a single amber LED signal color for readouts and
active states, mint reserved for transport/play, red for record. One committed
dark theme, painted explicitly.
