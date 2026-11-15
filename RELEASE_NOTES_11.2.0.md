# PianoToLife 11.2.0

**The MEDIA player becomes a practice studio: lyrics found and corrected, transposition, any format.**

- **LYRICS**: the lyrics of a piece found by listening to its separated voice (whisper.cpp with the Whisper *small*
  model, on your computer). The model (488 MB) is downloaded the first time. LANG: automatic, or the language sung.
  The `.lrc` goes beside the audio file (asked before replacing one), and SCREEN shows it. The LYRICS button lights up
  when the piece has its lyrics.
- **LYRICS EDIT**: the real lyrics from LRCLIB, aligned on the voice with the engine of the author's AI-LYRICS-FIX
  (LRC SYNC when LRCLIB has its own times, SMART for a plain text). Choose another result, change the text, TAP, OFFSET,
  SAVE.
- **TRANSPOSE**: -6 to +6 semitones, its tempo kept, live, after the A4 tuning. A MIDI take stays in time; the stems,
  the BOUNCE with the audio, CHORDS and MAGIC VIEW follow. Remembered for each piece.
- **FOLDERS**: your folders of pieces as playlists, one click to switch. **Playlist SEARCH** (click the piece's name):
  as you type, without case, accents or punctuation.
- **FFmpeg (optional)**: when macOS or Windows cannot read a file, PianoToLife uses the FFmpeg installed on your computer
  (found by itself, or chosen in LOAD > FFmpeg). Files with several audio tracks: the track is asked once, then a
  right-click on the name changes it; each track has its own stems, lyrics, chords and levels.
- **SCREEN**: LYRICS ON / OFF (a video may already show its own words).
- **Quieter levels**: LEVEL and BOUNCE's Normalise also at -20, -21 and -22 LUFS; the media's CEIL. down to -7 dB, the
  bounce's true peak down to -7 dBTP.

**Internet:** PianoToLife uses the Internet only when you ask: to download the Whisper model once (from Hugging Face),
and when EDIT looks for lyrics on LRCLIB (only the artist, the title and the length of the piece are sent). Nothing
else, and nothing about you.

Manuals updated for 11.2.0: [User Manual](https://github.com/owfrappier/PianoToLife/blob/main/USER_MANUAL.md) · [Manuel d'utilisation](https://github.com/owfrappier/PianoToLife/blob/main/MANUEL.md) · [Sampler Manual](https://github.com/owfrappier/PianoToLife/blob/main/SAMPLER_MANUAL.md) · [Manuel du sampler](https://github.com/owfrappier/PianoToLife/blob/main/MANUEL_SAMPLER.md).

## Also in 11.1.7 and 11.1.6

- **11.1.7**: the standalone watches the sample rate (your preferred rate kept, a change said, RESTART AUDIO when the
  sound card changes it silently); BOUNCE: silence before the music.
- **11.1.6**: the diapason explained after a capture, takes named by their date, SYNC from REC, lighter keys under the
  pedal.

The full history: [CHANGELOG.md](https://github.com/owfrappier/PianoToLife/blob/main/CHANGELOG.md).

## Distributing sampled pianos made with PianoToLife

Making sample sets with PianoToLife and playing them for your own use is free. Any public distribution of a sampled piano made for PianoToLife's sampler (sample sets, `.ptlset` / `.wptl` files, `[SAMP]` presets), **free or paid, requires my prior authorization.** Please contact me at pianotolife@outlook.com before publishing anything: together we will set up its protection (encrypted container, password) and the way it is distributed.

## Download

See the assets below (Mac: AU, VST3, standalone; Windows: installer, VST3, standalone).
