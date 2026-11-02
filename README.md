# Awesome Audio to MIDI [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of tools that turn audio into MIDI — online converters, open-source
> models, desktop apps, DAWs and plugins. Everything here was opened and checked by a
> human; anything unverified is not listed.

Audio-to-MIDI is not one problem. It is at least four: monophonic pitch tracking,
polyphonic piano transcription, drum transcription, and full-mix transcription. Tools
that are excellent at one are usually poor at another, and almost no marketing page
says which one it solved. Every entry below therefore states **what it takes in, what
it produces, and where it runs**.

## Contents

- [What "audio to MIDI" actually means](#what-audio-to-midi-actually-means)
- [Online converters](#online-converters)
- [Open-source models and libraries](#open-source-models-and-libraries)
- [Desktop apps](#desktop-apps)
- [DAWs with built-in extraction](#daws-with-built-in-extraction)
- [Plugins](#plugins)
- [Audio to sheet music](#audio-to-sheet-music)
- [Supporting tools](#supporting-tools-source-separation-notation)
- [Datasets and evaluation](#datasets-and-evaluation)
- [How to choose](#how-to-choose)
- [Contributing](#contributing)

## What "audio to MIDI" actually means

Before comparing tools, decide which of these you need. Most disappointing results come
from using a tool built for one row on a different row.

| You have | You want | The real problem |
| --- | --- | --- |
| One instrument, one line (vocal, flute, guitar solo) | A melody line as MIDI | Pitch tracking. Well solved. |
| Solo piano recording | Both hands as MIDI | Polyphonic transcription. Hardest common case. |
| Drum loop or kit recording | Kick/snare/hats as MIDI | Onset classification. A different model family. |
| A finished song with many instruments | MIDI for several parts | Must be separated first; no model handles this cleanly in one pass. |
| Any of the above | Printed sheet music | A second problem: MIDI is not notation. See [Audio to sheet music](#audio-to-sheet-music). |

## Online converters

Browser-based. No install. Check the **privacy** column before uploading anything you
care about — "free online converter" says nothing about where your file goes.

| Tool | Input | Output | Processing | Notes |
| --- | --- | --- | --- | --- |
| [NoteMidi](https://notemidi.com/) | Audio file | MIDI, sheet music | In browser | Free. Audio is not uploaded; model runs locally. Author's project — see [disclosure](#disclosure). |
| [Basic Pitch (web demo)](https://basicpitch.io/) | Audio file, or record | MIDI | In browser | Official demo of Spotify's model. The reference point everything else is measured against. |
| [Piano Scribe](https://piano-scribe.glitch.me/) | Audio file | MIDI | Server | Demo of Magenta's Onsets and Frames. Piano only. |
| [jukeblocks](https://jukeblocks.io/free-tools/audio-midi-converter/) | Audio file | MIDI | Server | Free tier inside a larger tool site. |
| [Klangio](https://klang.io/) | Audio file | MIDI, sheet music, tabs | Server | Paid tiers; strong on notation output. |
| [Songscription](https://songscription.ai/) | Audio file | MIDI, sheet music | Server | Paid; aimed at full arrangements. |
| [Melody Scanner](https://melodyscanner.com/) | Audio file | MIDI, sheet music | Server | Free tier, paid export. |
| [Muscriptor](https://muscriptor.kyutai.org/) | Audio file | MIDI | Server | Research demo; one of the few aiming at full mixes. |
| [PixelTools](https://pixeltools.io/audio-to-midi/) | Audio file | MIDI | In browser | Part of a multi-tool site. |

## Open-source models and libraries

Run these yourself. This is where the actual capability lives — most commercial
converters wrap one of these.

| Project | Language | What it does | License note |
| --- | --- | --- | --- |
| [spotify/basic-pitch](https://github.com/spotify/basic-pitch) | Python | Instrument-agnostic transcription, MIDI out. The de-facto baseline. | Apache-2.0 |
| [DamRsn/NeuralNote](https://github.com/DamRsn/NeuralNote) | C++ / JUCE | Basic Pitch as a VST3/AU/standalone plugin, with MIDI editing | See repo |
| [magenta/onsets_frames_transcription](https://github.com/magenta/magenta/tree/master/magenta/models/onsets_frames_transcription) | Python | Piano and drums, strong on onset detection | Apache-2.0 |
| [Omnizart](https://music-and-culture-technology-lab.github.io/omnizart-doc/) | Python | Multi-instrument transcription suite (piano, drums, vocal, chord) | MIT (see repo) |
| [sonic-visualiser/tony](https://github.com/sonic-visualiser/tony) | C++ | Melody transcription, tightly integrated with Sonic Visualiser | GPL |
| [justinsalamon/audio_to_midi_melodia](https://github.com/justinsalamon/audio_to_midi_melodia) | Python | Melody extraction to MIDI | See repo |
| [BShakhovsky/PolyphonicPianoTranscription](https://github.com/BShakhovsky/PolyphonicPianoTranscription) | Python | Piano, RNN-based | See repo |
| [BShakhovsky/PianoAudioToMidi](https://github.com/BShakhovsky/PianoAudioToMidi) | Python | Piano transcription | See repo |
| [corbanbrook/spectrotune](https://github.com/corbanbrook/spectrotune) | JS | Polyphonic pitch detection, browser-friendly | See repo |
| [svsdval/video2midi](https://github.com/svsdval/video2midi) | Python | MIDI from Synthesia-style videos, not from audio | See repo |
| [HemantKArya/Melodfy](https://github.com/HemantKArya/Melodfy) | — | Transcription utility | See repo |
| [WaoN](https://sourceforge.net/projects/waon/) · [waonc](https://github.com/ahlstromcj/waonc) | C | Phase-vocoder based transcription; old, still works on clean monophonic input | GPL |

Longer tail of small and academic projects: [natowi's list](https://gist.github.com/natowi/d26c7e97443ec97e8032fb7e7596f0b0)
of open-source audio-to-MIDI packages.

## Desktop apps

<!-- Each entry must be opened and verified before this section goes public. -->
- Melodyne (Celemony) — pitch and time correction first, audio-to-MIDI second. Accurate on monophonic material; not designed for transcription.
- AnthemScore — automatic transcription to score and MIDI.
- Samplab — sample editing with note extraction.
- RipX DAW (Hit'n'Mix) — note-level editing of mixed audio.
- ACE Studio — AI voice workbench with MIDI extraction.
- Dubler 2 — microphone-to-MIDI for beatboxing and humming.
- Jam Origin MIDI Guitar — real-time guitar-to-MIDI.
- Transcribe! — playback and analysis aid for transcribing by ear, not automatic.

## DAWs with built-in extraction

Most DAWs can convert audio to MIDI, with very different quality. Useful to know before
buying a dedicated tool:

- Ableton Live — audio-to-MIDI conversion for melodic and harmonic material, and drum-to-MIDI.
- Logic Pro — Flex Pitch to MIDI.
- FL Studio — Edison and slice-based conversion.
- Cubase — VariAudio to MIDI.

## Plugins

- [NeuralNote](https://github.com/DamRsn/NeuralNote) — VST3/AU/standalone, Basic Pitch inside, with piano-roll editing. Open source and free.

## Audio to sheet music

A separate output problem: notation needs quantisation, key, rests and ties that MIDI
does not contain.

- [miditoolbox](https://miditoolbox.com/score) — MIDI in, PDF and PNG out.
- [ConvertCrunch](https://convertcrunch.com/) — MIDI in, MusicXML out, in browser; no PDF.
- [Soundslice](https://www.soundslice.com/) — notation editor with import.
- [TuneScribers](https://tunescribers.com/) and [Nutif](https://nutif.ai/) — human-assisted and automated transcription services.

## Supporting tools: source separation, notation

Transcription quality jumps if you separate first.

- [Spleeter](https://github.com/deezer/spleeter) — stem separation (vocals/drums/bass/other).
- [Musisep](https://github.com/rgcda/Musisep) — source separation.
- [MuseScore](https://musescore.org/) — open-source notation editor; opens MusicXML and MIDI.
- [Verovio](https://www.verovio.org/) — engraving library; renders MusicXML in a browser.
- [OpenSheetMusicDisplay](https://opensheetmusicdisplay.org/) — MusicXML renderer for web apps.

## Datasets and evaluation

- [Slakh](http://www.slakh.com/) — synthesized multi-track audio with ground-truth MIDI.
- [MAESTRO](https://magenta.tensorflow.org/datasets/maestro) — piano performances with aligned MIDI.
- [MAPS](https://github.com/valentinradu/MAPS) — piano audio with aligned MIDI.
- [MIR evaluation resources](https://github.com/mir-evaluation/mir_eval) — standard metrics.

## How to choose

1. **Single line or full mix?** If it is one instrument or a voice, nearly any tool works. If it is a mix, separate stems first.
2. **Do you need the file back, or do you need to hear it?** MIDI is editable; sheet music is printable. They are different deliverables.
3. **Where does your audio go?** Browser-local means nothing leaves your machine in transit. Server-side means it does. Check one request in devtools instead of trusting a badge.
4. **What can you do with the output?** A note list you cannot quantise or correct by hand is not usable. Editing matters more than raw note accuracy.

## Contributing

Read [contributing.md](contributing.md). In short:

- One line per entry: `[Name](link) - What it takes in, what it produces, where it runs.`
- No superlatives. No "best", "powerful", "revolutionary". Describe, do not advertise.
- The link must be to the tool itself, not to a blog post about it.
- Disclose anything you built or are paid for. Undisclosed self-promotion is removed.

## Disclosure

Maintained by the team behind [NoteMidi](https://notemidi.com/). NoteMidi is listed in
[Online converters](#online-converters) with that fact marked in the table. Tools are
added because they exist and work, not because of any relationship with this project.
Corrections and removals are welcome via issue.
