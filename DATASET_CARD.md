# Dataset Card: Awadhi Speech Dataset v1.0

## Summary
6,448 MP3 clips (~18.9 h) of Awadhi speech with draft Devanagari transcripts and English translations, for ASR and TTS research.

## Collection
Audio was collected from publicly available Awadhi recordings (storytelling, conversation, folk singing, oratory), then segmented into 4.1–22.2 s clips.

## Files
- `data/metadata.csv`: one row per clip (transcript, translation, speaker/environment/style/emotion labels, `tts_usable`, `needs_review`, `has_unclear_segments`).
- `data/transcriptions.jsonl`: per-clip audio quality stats (duration, sample rate, SNR, loudness, clipping, speech ratio, MD5).
- `data/samples/audio/`: 25 example clips. Full audio is on the Releases page.
- `scripts/transcribe_awadhi.py`: draft-transcription pipeline.

## Annotation and quality
Transcripts are machine-generated drafts (Whisper with language forced to Hindi) and often render Awadhi words the Hindi way. Labels are automatic or semi-automatic and not verified by native speakers. 1,422 clips are flagged `needs_review`; 3,177 clips are flagged `tts_usable`.

## Known limitations
- ~88% male speakers; few female and child voices.
- Skewed toward storytelling and conversation; little read speech.
- Mixed recording quality; filter on `environment` and the quality stats.

## Terms and contact
Evaluation use only; do not redistribute. Contact: arooj@presense.us
