# Awadhi Speech Dataset

An open-in-spirit speech corpus for **Awadhi**, a Hindi-belt language spoken by tens of millions of people in eastern Uttar Pradesh, with almost no representation in today's speech technology.

**Project Awadhi** aims to make Awadhi a first-class language for speech recognition (ASR) and text-to-speech (TTS). This repository contains the first release of the dataset and the tooling used to build it.

## Why this matters

Awadhi is the language of the Ramcharitmanas and a rich oral tradition of folk songs, storytelling and everyday speech. Despite its large speaker base, no Awadhi-native ASR or TTS system exists. Existing multilingual models treat it as Hindi, which loses its vocabulary, pronunciation and identity. Building one starts with data, and there is very little to start from.

## Dataset at a glance

| | |
|---|---|
| Clips | 6,448 |
| Total duration | ~18.9 hours |
| Clip length | 4.1 – 22.2 s (mean 10.6 s) |
| Source recordings | 775 |
| Audio format | MP3, 44.1 kHz, stereo |
| Transcripts | Devanagari, with English translation |
| Flagged for human review | 1,422 clips (`needs_review`) |

**Speaking styles:** storytelling (2,673), conversational (2,468), singing/chanting (616), read speech (288), oratory (270).

**Recording environments:** quiet indoor (4,233), studio (1,175), outdoor (643), stage/broadcast (227), noisy indoor (113).

**Speakers (as labeled):** male 5,676 · female 608 · mixed 61 · unknown 103. Age groups: adult 4,195 · elderly 1,852 · young adult 293 · child 5 · unknown 103.

**Emotion (as labeled):** calm 2,962 · neutral 2,729 · happy 431 · sad 164 · excited 107 · angry 18 · other 37.

## Repository layout

```
data/
  metadata.csv           # one row per clip: transcript, translation, annotations
  transcriptions.jsonl   # per-clip audio quality stats (SNR, loudness, clipping, MD5)
  samples/audio/         # a small set of example clips
scripts/
  transcribe_awadhi.py   # draft-transcription pipeline
docs/
  stats.md
DATASET_CARD.md          # collection process, fields, limitations
```

The full audio (~1.6 GB) is attached to the **Releases** page as `awadhi-speech-audio-v1.0.zip`. Verify the download with `checksums.txt`.

## Metadata fields (`data/metadata.csv`)

| Column | Description |
|---|---|
| `file_name` | Audio file name, matching the file inside the release zip |
| `transcription_devanagari` | Awadhi transcript in Devanagari |
| `english_translation` | English translation |
| `duration_sec` | Clip length in seconds |
| `speaker_gender`, `speaker_age_group` | Annotated speaker attributes |
| `environment`, `speaking_style`, `emotion` | Annotated recording attributes |
| `tts_usable` | `True` if the clip is clean enough for TTS training |
| `needs_review` | `True` if the transcript needs human verification |
| `has_unclear_segments` | `True` if parts of the audio are hard to make out |


## Roadmap and what sponsorship would enable

1. **Native-speaker review** of all transcripts, starting with the 1,422 flagged clips, to produce a gold-standard subset.
2. **More data**, especially female, young and child speakers and read speech.
3. **Baselines:** fine-tuned ASR and a first Awadhi TTS voice trained on the `tts_usable` subset.
4. **Public benchmark** with a held-out test split, so progress on Awadhi can be measured.
