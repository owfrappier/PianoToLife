<h1 align="center">PianoToLife</h1>
<p align="center"><i>formerly SympResHost</i></p>
<p align="center"><b>Bring your VST / AU piano to life — and to realism.</b></p>
<p align="center">Replace your piano's static sympathetic resonance samples and canned pedal behaviour<br>
with one live, physically modelled string engine — from a single held key to every damper lifted.</p>
<p align="center"><b>New in 10:</b> no hosted piano needed — play your own samples with the built-in sampler.<br>Pedal-up samples are enough: resonance, pedals and noises are modelled live (hybrid sampling + modelling).</p>

<p align="center">
  <img src="Screenshot-A.png?v=1131" alt="PianoToLife: the main window (SAMPLER mode, a sampled Steinway B)" width="900">
</p>

<p align="center">
  <a href="../../releases/latest"><b>⬇ Download the latest release</b></a> ·
  macOS 14+ (Apple Silicon) · Windows 10/11 x64 · AU · VST3 · Standalone
</p>
<p align="center">
  📖 <a href="USER_MANUAL.md"><b>User Manual</b></a> · <a href="MANUEL.md">Manuel (FR)</a> ·
  <a href="SAMPLER_MANUAL.md"><b>Sampler Manual</b></a> · <a href="MANUEL_SAMPLER.md">Manuel du sampler (FR)</a>
</p>
<p align="center">
  PianoToLife is free. <a href="https://www.paypal.com/paypalme/owfrappier"><b>♥ Donate with PayPal</b></a> to support its development.<br>
  New in 11: the <b>MEDIA</b> player (recordings and videos, lyrics, chords, NO VOICE / NO PIANO) is an option — 29 EUR or 29 USD minimum, one payment, no subscription.<br>
  ✉️ Password after your donation, no PayPal in your country, any question: <a href="mailto:pianotolife@outlook.com"><b>pianotolife@outlook.com</b></a>
</p>

<p align="center">
  <a href="https://www.youtube.com/watch?v=PwUajB3f9ZY">
    <img src="https://img.youtube.com/vi/PwUajB3f9ZY/maxresdefault.jpg" alt="Video: Chopin Nocturne Op. 48 No. 1 through PianoToLife" width="640">
  </a><br>
  <b>▶ Video: Chopin, Nocturne Op. 48 No. 1, played through PianoToLife</b> — with MAGIC VIEW and its staff
</p>

> **Who is PianoToLife for?** It is made for **sampled pianos** — the libraries you already own, or your own piano,
> which you can sample with up to 5 microphones. Its auto-mapping places the velocities, the attacks, the tonal colours
> and the dynamics as on a real piano: a fast and powerful sample editor, built on a sampling / modelling approach.
> Purely modelled pianos already compute their own resonance and pedal behaviour, so PianoToLife
> has little to add to them: it is not intended for hosting them.

## Only pedal-up samples: the rest is modelled

In **SAMPLER** mode, **all you need is the pedal-up notes** of a piano: drop them in, and PianoToLife maps them by
listening to them. It finds each sample's key, places the velocity layers and aligns the attacks of every layer and
microphone. **Everything else is modelled live**:

- sympathetic resonance;
- sustain pedal (half pedal included) and pedal noise;
- una corda;
- release and dampers.

That is the advantage of this **hybrid sampling + modelling** approach: the realism of real recordings for the strike
and its tone, and a live, physical behaviour for everything that happens around it, without hundreds of pedal-down,
release or resonance samples. A 3- to 6-layer pedal-up library is enough: PianoToLife smooths the steps between layers
so it plays like a deeply sampled piano, even when the library is badly cut or normalised.

<p align="center">
  <img src="Screenshot-E.png?v=1131" alt="SAMPLER EDIT: the DRY / DENOISE / BODY panel" width="900">
</p>


## The MEDIA player: play along with any recording

Load a song, a playlist, a folder or a video, and play your piano with it. The MEDIA player is an option of PianoToLife
(29 EUR or 29 USD minimum, one payment, no subscription; 3 minutes of demo per session without the password).

<p align="center">
  <img src="Screenshot-B.png?v=1131" alt="The MEDIA player: PADS, FOLDERS, LEVEL and CEIL., Play at A4 and TRANSP., NO VOICE / NO PIANO / CLEAN PIANO, LYRICS" width="640">
</p>

- **NO VOICE / NO PIANO / CLEAN PIANO**: the piece separated once on your computer (kept in the stems folder: Samples/Stems, or a folder you choose, shared on the network), then played
  without its voice, or without its piano so that you play the piano part.
- **In tune and in your key**: *Play at A4* plays the recording at the A4 of your piano (432 to 448 Hz), and **TRANSP.**
  moves it up to 6 semitones higher or lower, its tempo kept. Both are remembered for each piece.
- **LEVEL and CEIL.**: every file at the same loudness (-14 to -23 LUFS), its own true-peak ceiling (-1 to -7 dB).
- **REC and PLAY with the MIDI**: your take and the recording start together; BOUNCE can put the recording in the file.
- **FOLDERS** and **SEARCH**: your folders of pieces as playlists, **virtual folders** (PLAYED, STEMS READY and your own
  lists), and a search that ignores case, accents and punctuation; the pieces already separated show a green dot.
- **PADS**: your pieces, videos and jingles on 80 pads, launched with a click or your MIDI controller — in the player
  (MEDIA) or over everything (PAD).
- **Any format, any audio track** (optional): with FFmpeg installed on your computer, PianoToLife also reads MKV, WebM,
  Opus, APE, WavPack, DSD… shows the picture of any video (AV1, MKV, WebM...) and lets you choose the audio track of a
  film in several languages.

<p align="center">
  <img src="Screenshot-F.png?v=1131" alt="PADS: 4 x 4 pads on 5 pages, a MIDI controller, MEDIA or PAD, TOGGLE or HOLD, MIDI LEARN" width="640">
</p>

> **Disk space.** A file that macOS or Windows cannot read directly — a video's sound (MP4, MOV...), a format decoded by
> FFmpeg (MKV, WebM, Opus...) or another audio track of a film — is decoded **once and kept** in a cache on your
> computer, so that it plays, jumps and is analysed at once afterwards: on a Mac in `~/Library/Application Support/
> PianoToLife/Video sound`, on Windows in `%APPDATA%\PianoToLife\Video sound`. The 30 newest are kept; a long film can
> take more than a gigabyte, so delete that folder whenever you like (it is made again when needed). Ordinary files
> (MP3, FLAC, WAV, AIFF, M4A...) are read directly and never copied. The separated pieces (NO VOICE / NO PIANO,
> 150–200 MB each) and the Whisper model (488 MB) go to your samples folder, in **Stems** and **Whisper**: choose a
> large disk for it.

<p align="center">
  <img src="Screenshot-D.png?v=1131" alt="SCREEN with the lyrics, CHORDS, the MEDIA player and MAGIC VIEW with its staff" width="900">
</p>

- **CHORDS**: the chords and the key of the piece, scrolling in time with it (and transposed with it).
- **MAGIC VIEW**: the notes of the separated piano (or voice, or other instruments) falling onto a keyboard, with a
  staff.
- **SCREEN**: a window for a second screen — the lyrics in time with the piece, over its video if it has one.

### LYRICS: found, corrected, in time

<p align="center">
  <img src="Screenshot-C.png?v=1131" alt="LYRICS EDIT: the lyrics proposed by LRCLIB on the left, aligned on the voice on the right" width="900">
</p>

- **LYRICS** listens to the separated voice of the piece and writes its lyrics in time (Whisper, on your computer). The
  result is a standard `.lrc` file beside the audio file, so other programs can read it too.
- **EDIT** looks for the real lyrics on LRCLIB (a free lyrics database), proposes the best ones (or others to choose),
  and aligns them on the voice heard: green words are found in the voice. Change the text, set a line's time with
  **TAP** while it plays, move them all with **OFFSET**, then **SAVE**.
- The lyrics are for your personal use only: PianoToLife never distributes lyrics.

---

## What's new in 11.3.1

**A fluid media player on network folders, MIDI files played as in a DAW, and LISTEN on a range of velocities.**

- **Network folders** (a PC playing a Mac's shared folders, or the other way round): pieces, stems and lists on a
  network drive are now read in the background, so the window never freezes. On Windows, mapped network drives (M:,
  S:...) were not recognised as network drives before.
- **The next piece prepared while one plays**, with its stems and lyrics: NEXT and the end of a piece go on at once.
- **PADS in memory**: the files of the page shown are read beforehand, so a pad starts at once, even from a network
  folder.
- **Folders open at once**: a folder's list is kept while it does not change, and changing virtual folder is immediate.
  FOLDERS ticks the folder or the virtual folder you chose.
- **STEMS READY** shows a piece as soon as it is separated.
- **MIDI files played on one channel**, as a DAW track does: in a file whose sustain pedal is on another channel than
  its notes, the pedal now holds them (an option in LOAD MIDI's menu, on by default).
- **LISTEN** (SAMPLER EDIT) **from one velocity to another**: right-click LISTEN for a two-handle slider, with ALL, THIS
  LAYER and ITS BOUNDARY (the transition between the layer selected and the next one).
- The player's line names the real stems folder; a new piece starts exactly as it is (no fade-in); the loading bar no
  longer stays shown after EXPAND.

### Also in 11.3.0

**FIX KEYS for pianos recorded out of tune, your hosted piano's tuning exported key by key, stems shared between two computers, and a cleaner media player.**

- **FIX KEYS** (TEMPERAMENT, SAMPLER mode): for a piano recorded with some keys out of tune. Each key's own error,
  apart from the piano's stretch and the temperament it was recorded in, is measured and corrected. The correction is
  shown beside its Tune in EDIT; your Tune is not changed. Any temperament and the Stretch then apply to clean keys.
  **Stretch 100 %** keeps the stretch this piano was tuned with, as a good tuner does; 0 % gives exact octaves.
  **AS RECORDED** plays the piano as recorded, and **CLEAR FIX** removes the corrections. Undoable.
- **The tuning of the hosted piano** (TEMPERAMENT, HOST mode): measured on its Piano Model: its A4, its stretch, and the
  keys off its line. Choose a temperament in **Tune it to**, with the Stretch and FIX KEYS, then **EXPORT** the table of
  corrections: a `.txt` key by key, to type into the hosted piano's own Tune of each key, and a Scala `.scl` + `.kbm`,
  for pianos that load Scala files. The values are rounded to 0.1 cent or 1 cent.
- **Check by ear** and the capture measure the samples as recorded, whatever temperament is played, so there is no
  false alarm after a temperament change.
- **Stems found by their content**: a piece that is moved, renamed or played on another computer finds its stems and
  lyrics again. Stems separated before 11.3.0 are found too. **Right-click FAST / QUALITY** to choose the stems folder:
  a folder shared on the network lets a Mac and a PC use the same stems.
- **Pieces and stems played from memory**, as DJ software does: the disk is free while you play. A folder or a virtual
  folder on the network is read in the background, so the player never waits for the network.
- **No click at PLAY or STOP.** The piano's REVERB, EQ and COMP also start from rest when switched back on.
- **"PianoToLife cannot keep up"**: audio dropouts are now told apart from a real change of the sound card's rate, with
  advice (buffer size, power plan) and a *Don't show again* option.
- **MIDI files**: pitch bend, tuning messages (RPN / NRPN) and SysEx meant for a sound module are ignored (an option in
  MIDI LOAD's menu). An old General MIDI file no longer detunes the piano.
- **STEMS READY** lists each separated piece once.

<p align="center">
  <img src="Screenshot-G.png?v=1131" alt="TEMPERAMENT (SAMPLER): Equal, Stretch 100 %, FIX KEYS and CLEAR FIX, the table Recorded / Played / Shift" width="640">
</p>

<p align="center">
  <img src="Screenshot-H.png?v=1131" alt="TEMPERAMENT (HOST): the hosted piano tuned to Equal, Stretch 100 %, FIX KEYS, EXPORT .txt + .scl" width="640">
</p>

### Also in 11.2.6

**Lyrics without separating, your windows on any screen, RESET STEMS / RESET LYRICS, and measured speeds.**

- **LYRICS without separating first**: on a piece not separated yet, LYRICS asks **BEST** (the voice separated first,
  the most accurate) or **FASTER** (the whole piece heard at once — handy on a computer without a graphics card; correct
  the result with EDIT). *Remember my choice*; changed in LANG's menu.
- **The window buttons open and close**: CHORDS, SCREEN, PADS, MAGIC VIEW and VIEW open their window, a second click
  closes it, and the button stays lit while its window is open.
- **A window lost on a screen switched off**: right-click on a lit button — **Bring it to this screen**, or **Move it to
  screen 2, 3...** (each screen with its size).
- **RESET STEMS** and **RESET LYRICS** (under FAST / QUALITY): the separated tracks, or the lyrics PianoToLife found, of
  the piece playing deleted, to make them again. RESET STEMS keeps the lyrics; a `.lrc` of your own is never deleted.
- **LYRICS on a laptop's graphics card** (Windows): Whisper took the first graphics card it found, often the laptop's
  integrated one; it now uses the dedicated card (NVIDIA / AMD) — about 6 s instead of about a minute for a piece of 3 min 25.
- The separation times shown are corrected: QUALITY about half of the piece's length, FAST about a quarter (M2 Pro).
- **Measured speeds**, and which computer for the stems: see [Requirements](#requirements).

### Also in 11.2.5

**PADS for the live, and your separated pieces at a glance.**

- **PADS** (left of FOLDERS): 4 x 4 pads on 5 pages that slide. Drop audio or video files on them — each pad shows the
  cover or a picture of the video — and play them with a click or your **MIDI controller (MIDI LEARN** per pad and for
  the pages; it works with the window closed). **MEDIA** pads play in the media player (stems, lyrics, SCREEN...);
  **PAD** pads play over everything and add up (their own level). **TOGGLE** (a click plays, another one stops) or
  **HOLD** (plays while held).
- **No pop, no click**: 100 ms fades when a pad starts or stops, and each piece of the player comes in smoothly.
- **STEMS READY**: a virtual folder that fills itself with the pieces already separated — and everywhere, a **green dot
  and bold names** show the pieces whose NO VOICE / NO PIANO is instant.

### Also in 11.2.4

**Karaoke lyrics, no separation you didn't ask for, and Check by ear at any tuning.**

- **SCREEN karaoke**: the line sung fills as it is sung (on the words Whisper heard when they are there), and the lines
  glide up smoothly. **OFFSET** in SCREEN's bar: the lyrics shown up to 1 s earlier or later (for all pieces; the
  `.lrc` is not changed).
- **No separation you didn't ask for**: each new piece (and each start) begins with NO VOICE and NO PIANO off — nothing
  is separated without a click. CLEAN PIANO keeps your choice.
- **Virtual folders**: a virtual folder can be the source too — add a whole list to another one (Cmd / Ctrl + A, ADD).
- **Check by ear at any SR A4 Tuning** (thanks to a user's precise report): it measured the keys at the Piano Model's own
  pitch, so far from it (350 Hz...) it reported big differences that did not exist. It now follows SR A4 Tuning and
  Fine Pitch, and the unison of the high keys. Your Piano Models were right: nothing to capture again.
- The `.lrc` written by EDIT says where its times come from: Whisper, or LRCLIB.

### Also in 11.2.3

**Virtual folders, the media at the LUFS you choose, and the DRY version kept.**

- **VIRTUAL FOLDERS** (in FOLDERS): **PLAYED**, the 500 pieces played last, newest first (remove what you don't want),
  and **your own lists**, named as you like, filled from your folders (with a search) or from anywhere on the disk.
  Only links: nothing is copied. Each list is an `.m3u` file (VLC, Music... read it too).
- **The media at the LUFS you choose**: the player's VOL starts at **0 dB** (it was -6 dB, under the LEVEL chosen), goes
  back to 0 dB when LEVEL or CEIL. changes, and a double-click puts it at 0 dB. First opening: LEVEL **-20 LUFS**,
  CEIL. **-7 dB**.
- **SAMPLER: the version kept** (ORIG. / DRY n): each instrument comes back with the version it played last — when you
  choose it again in the list, and when you come back from HOST mode (it came back as ORIG.).

### Also in 11.2.2

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

**And in 11.2.2**

- **Every video shows its picture**: when macOS or Windows cannot decode a video's pictures (AV1 on a Mac M1 / M2 — many
  recent YouTube videos —, MKV, WebM, AVI...), PianoToLife decodes them with the FFmpeg installed on your computer, as it
  plays, with nothing written on the disk. Without FFmpeg, SCREEN says so instead of staying black.
- **Full screen on one screen only**: FULL SCREEN (SCREEN, CHORDS, MAGIC VIEW) now covers exactly the screen the window is
  on; the other screens stay as they are (the macOS full screen could turn them black).
- **Lyrics of videos found more often**: titles like "Song (Live at ... 1998) Alternate Version-(1080p60)" are cleaned
  before asking LRCLIB.
- **No more lags with very large folders**: the media player's playlist has its own file (it was inside the settings,
  read and written again at each piece). The settings file is cleaned at the first start.
- **No tooltips in the compact view**, made for playing.

### Also in 11.1.7

**The standalone now watches the sample rate: another program can no longer put PianoToLife out of tune without you
knowing.**

- **Your preferred sample rate**: the standalone remembers the sample rate you choose in Options > Audio/MIDI Settings
  (never one imposed by another program). At start-up, if the sound card opens at another rate, PianoToLife sets it back
  and tells you, or tells you why it couldn't (another program holding the card).
- **Sample rate changed while playing**: when another program (a DAW opening a project at 48 kHz...) or the sound card
  itself changes the rate, PianoToLife follows and says so once.
- **And when nobody tells it**: some systems and drivers change the rate without telling the applications (more often on
  Windows). Everything then sounds out of tune. PianoToLife now measures the sound card's real rate itself and, if it no
  longer matches, offers **RESTART AUDIO**. It costs nothing in CPU.
- **BOUNCE: silence before the music** (right-click on BOUNCE): none, 0.5 s or 1 s, for a piece that starts on its very
  first note (some players cut the first milliseconds).

The VST3 and AU were already safe: the DAW sets the sample rate and tells the plugin, and PianoToLife recomputes
everything at the new rate.

### Also in 11.1.6

**The diapason explained, takes named by their date, SYNC from REC — and lighter keys under the pedal.**

- **The diapason, said clearly**: at the end of a capture, when the piano is not at 440 Hz, PianoToLife says the A4 it
  detected and how the Piano Model plays it (HOST: stored at the absolute reference A4 = 440 Hz and retuned in real time
  to SR A4 Tuning; SAMPLER: the samples' own tuning). The .srpiano file explains it too (a new "tuningNote" line), and a
  SAMPLER capture writes its real "referenceA4Hz". Nothing changes in the sound.
- **Takes named by their date**: the save window of a take now proposes *P2L-date-time.mid*, as REC stopped from the MIDI
  controller does.
- **SYNC from REC**: right-click on REC → "REC and PLAY with the audio of the MEDIA player (SYNC)", the same setting as
  in the MEDIA window.
- **Keys kept by the pedal lighter** (a GitHub suggestion): with the velocity colours, the keys that only ring under the
  pedal are much paler, so the keys you play stand out.
- **Fix**: with the EQ panel open, REVERB's ALGO | IR buttons no longer cover the EQ curve.


The full history of the earlier versions: **[CHANGELOG.md](CHANGELOG.md)**.

## What it does

Most virtual pianos sound beautiful note by note, yet something is missing as soon as you
really *play*: the halo of strings ringing in sympathy, the bloom of the sustain pedal, the
way a chord changes colour as the dampers lift, the subtle breath of half-pedalling.
Built-in "sympathetic resonance" and "sustain resonance" options are often static,
generic, or simply absent.

**PianoToLife** hosts your favourite piano plug-in and adds a physically modelled
**sympathetic resonance and sustain engine** around it.

### Driven by the real sound of your piano

PianoToLife does not add a generic reverb or a canned resonance sample. The free strings
are set into vibration by **the actual audio of the piano you play**: every note, every
velocity, every nuance of the samples feeds the resonating strings in real time, exactly
as the soundboard of a real piano carries the vibration of one string to the others.

### Calibrated for each piano

Each piano can be **calibrated precisely** with the built-in **automatic capture**.
PianoToLife plays the **88 notes pedal up**, one by one, and analyses the real partials,
their tuning, their inharmonicity and their decay times. It then builds a resonance model
unique to that instrument (done once; rendered offline in the standalone since 10.7.0). Since 9.5.0 it also records
short strikes at up to 8 velocities (since 9.5.2 in the middle of the piano's real layers, found first on A4), which adapt the una corda to your piano, warns you if anything
clipped and cleans the model automatically. A model of a sampled concert
grand (V8) is included and ready to use.

Since 9.4.2 the resonance follows the exact partials of the model, string by string: **capture
a model for each piano you use**. With the model of another piano, many strings no longer
match and the resonance is clearly poorer.

Before capturing, set the hosted piano **as loud as possible without clipping**, with **no reverb,
compression or other effect**, and with **everything switched off that is not the plain note**
(release samples, sustain / pedal resonance, sympathetic resonance, key and pedal noises),
and with the piano's own **velocity curve set to linear** (no smear or progressive velocity).
Preferably the close microphones: room microphones put the hall into the model. If you play with hall microphones,
use PianoToLife's REVERB (ALGO or IR) to put the hall back.

**Models captured before 9.4.0:** they still work, but the capture is much richer since 9.4.0
(up to 255 partials per note instead of 48, the high harmonics of the bass strings that make
the "harp" of the sustain). Capture your piano again to get the new sound.

### Features

- **Every string can resonate.** The resonance comes from a model of the real partials of
  each string, measured from the piano you host. A held key frees its string; the pedal
  frees them all — exactly like the dampers of a real grand.
- **Real half-pedalling.** Resonance and damping follow the pedal continuously, from the
  first touch of the dampers to full sustain. In Host Sustain, held notes carry on as their
  own string with a fast-dying part and a long residue, like a real grand. Pedal-up / pedal-down transitions, chords
  caught in the pedal, syncopated pedalling and sostenuto behave naturally.
- **Pedal catch.** Press the pedal just *after* the notes and the strings still sounding
  feed the freed strings — gently, as on a real instrument. In Host Sustain, during a pedal
  change, a key released just before the pedal comes back down keeps its piano note; a note
  caught just after its release comes back through its own string, at a level that depends on how
  quickly you catch it; quick re-pedals fade naturally from one to the next. Keys still held when the
  pedal goes down (syncopated pedalling) bloom in about a second, with their own **Held** control.
- **Your piano's dampers.** **Undamped Keys Above** sets the last key with a damper, as on
  your piano: the strings above it ring freely and are never damped. The pedal frees every
  damped string below it (**Sustain Free To**), and with a **Bösendorfer Imperial** the left
  handle of Sustain Free To goes down to C0 to free its extra bass strings too.
- **Bass and treble dampers.** Damper Damping and Slope set how fast the dampers stop the
  strings, longer in the bass, shorter in the treble.
- **Natural string release.** When a damper falls, the partials of the string die away
  progressively instead of being cut. This includes the high harmonics, the duplex scale,
  the undamped treble strings and the slow beating of the bass unisons. It can replace
  weak or missing release samples, or blend with the ones your piano already has.
- **Honest colour.** Measured inharmonicity, per-string decay times, and the colour of strings
  driven through the bridge (not by the hammer), with up to 255 measured partials per note.
- **Selective coupling.** A free string answers only the partials that really match it, so
  neighbouring strings beat gently against each other as on a real piano. **Fullness** and
  **Shimmer** set how much the free strings answer on their low and upper partials.
- **Clear, accessible interface.** The detailed resonance settings fold away in a drawer and
  read **Default** at their default value, and the **DEFAULT** button in the drawer bar resets them all; the whole interface works with screen readers (Narrator / NVDA,
  VoiceOver) and from the keyboard.
- **Damper mechanics view.** A live, realistic view of the dampers and strings, at no
  CPU cost; the strings of the keys still held are shown in orange.
- **Efficient.** A highly optimised engine (about 2× faster since 8.2.11), plus an optional
  multicore mode that shares the resonance between CPU cores.
- **Compact view.** Fold the interface into a small bar while you play.
- **Una corda.** With **Una Corda: Simu**, the soft pedal works with any piano: a softer,
  rounder note adapted to each piano, and the unstruck string ringing in sympathy. With
  **Una Corda: BP**, your piano's own una corda samples play as before. Click the SOFT pedal to set its
  LEVEL and TONE to your taste (10.8.0).
- **Recorded Room AUTO CAL.** Measures the room recorded in your samples and puts everything PianoToLife adds in the
  same room, at the same level (10.8.0; called Ambience before 10.9.3). Not a reverb: REVERB (ALGO or IR) is the hall.
- **Layer detector and velocity calibration.** Find your piano's real velocity layers on A4
  in about 1 min 20 s, then calibrate its dynamics on a real concert grand, grand or upright;
  export the result as text. A large velocity curve, with your keyboard's real range (LEARN) stretched onto it
  (10.8.0).
- **Key and pedal noises.** A wooden key action (hammer back on its rest, key landing,
  repetition in the escapement), and a sustain pedal with its wooden thumps, the felts on the
  strings and the freed (mostly bass) strings ringing — following the pedal's travel and speed,
  each with its own volume.
- **Felt-Contact.** The felt touching a string that still vibrates when a key or the pedal lets
  the damper fall, made from each note's real partials and following your release speed, with
  its own volume and colour.
- **Listen to each part.** Full Piano = Piano Only + Half/rel/catch Pedal + Symp Res + Release + Noises + Room:
  hear any combination of parts, kept in the preset.
- **MIDI player (standalone).** Load, play, record and save MIDI, and bounce — offline, as fast as your computer can —
  to WAV, AIFF, FLAC or CAF, 16 or 24 bits / 44.1 kHz, to compare settings on exactly the same performance.
- **Take the room out of the samples (SAMPLER, 10.9.0).** DRY / DENOISE keeps the partials and their beats, protects
  the strike and takes out the room and the hiss, into a separate 24-bit FLAC container; then choose the room with the
  REVERB. The original samples are never touched.
- **Coherent fundamentals (10.9.3).** AUTO BODY measures the share of the fundamental of every sample and makes it
  coherent, layer by layer and key by key, with the piano's own proportion; GLOBAL gives back what close microphones lose.
- **Your own reverb (10.9.2).** Beside the Piano Hall, a zero-latency convolution reverb with the impulse responses
  you choose (WAV / AIFF / FLAC, mono, stereo, true stereo), level matched, DECAY and DAMP still at hand.
- **32-bit floating-point engine.** Everything — the hosted piano, the sampler, the resonance, the Recorded Room, the effects
  and the Ceiling — is processed in 32-bit float, so even the softest notes keep their full quality. BOUNCE renders in
  32-bit float, then writes 16 or 24 bits.
- **Output Ceiling and meters.** A transparent true-peak safety limiter, TRUE PEAK MAX and
  LUFS short-term / long-term, and an output level meter; OUTPUT stereo / swap / mono (10.8.1).

## Why sustain is not a separate effect

Many virtual pianos offer "sustain resonance" and "sympathetic resonance" as two separate
effects. On a real grand piano they are **one and the same phenomenon**. The sustain
pedal does nothing more than lift every damper at once:

| What you do | What happens inside the piano |
|---|---|
| One key held | One string is free to vibrate |
| A chord held | A few strings are free |
| Pedal down | **Every** string is free |
| Half pedal | Every string is free, but still lightly touched by the dampers |

One physical mechanism, simply more or fewer free strings, more or less damping.
PianoToLife models exactly that, with a single engine. That is why pedal-up / pedal-down
transitions, half-pedalling, chords caught in the pedal and a single held note all sound
natural. There is no switching or cross-fading between two effects, only the same strings
being freed or damped.

### The release, too

When a key is released or the pedal comes up, the dampers do not cut the sound like a
switch. The felt lands on the vibrating string and damps it progressively, some partials
dying faster than others depending on where the damper touches the string.
PianoToLife **re-creates this release**. The string's own partials, taken from the real
sound of your piano, die away gently as the damper settles, with a lighter or firmer touch
depending on how you release the key or the pedal. With half-pedalling, the dampers resting
lightly on the strings keep damping them softly instead of stopping them.

### Your piano's release, PianoToLife's release, or both

The release is part of the resonance: when a damper lands, the string and its harmonics die
away with the rest of the instrument. Release samples vary a lot from one virtual piano to
another (rich, weak or missing), so PianoToLife lets you choose with **Release Level**, right
under Resonance Level:

- **PianoToLife's release (recommended)**: turn the release off in your piano (e.g. release
  at −inf) and keep **Release Level** on. The release comes from the real partials of
  each string and follows the resonance, the dampers and the **Recorded Room**.
- **Your piano's own release**: untick **Release Level**, and keep the release of your piano.
- **A blend of both**: keep your piano's release a little lower and adjust **Release Level**
  around **Default**: PianoToLife adds what the samples lack (brighter high harmonics, the
  shimmer of the duplex scale, a longer, beating decay in the bass).

What the re-simulated release contains:

- **Up to 24 partials** of the string, taken from the real sound of your piano, continue
  and die away as the damper settles (**Fast** makes the damper contact more immediate).
- **Ring**: part of the energy passes through the bridge into the **undamped treble
  strings** and the **duplex scale**, which keep shimmering briefly, as on a real grand.
- **The duplex scale is already in your pedal-up samples**: the aliquot sections ring with
  every note, so they are part of each piano's recorded signature. The sympathetic resonance
  is built from those same samples (the Piano Model capture), so it carries your own piano's
  duplex colour too, not a generic one added on top. The **Ring** setting brings the duplex
  shimmer of the undamped keys out more or less.
- **In the bass**, the release lasts longer and the strings of a unison **beat** slightly,
  because they are never damped at exactly the same instant.
- **Release Weights** balances the colour of the release: 100 % keeps the partials as
  recorded; lower values bring up the high harmonics without changing the overall level
  (default 100 % since 9.4.0). It works like **Harmonic Balance** does for the resonance.
- **Release Decay** (in the drawer) sets the length of the release tail; it also follows
  Damper Damping and Slope, so it is longer in the bass.
- The release belongs to the resonance engine: switching **SYMPATHETIC RESONANCE** off
  switches it off too.

### Your release gesture counts

How fast you let a key come up changes how the damper lands, so PianoToLife listens to it:

- **Note-off (release) velocity** from keyboards that send it (Keyboard: **Release Velocity
  1-127**): a slow release gives a softer, longer damping; a quick one stops the string more
  firmly. An adjustable curve lets you match your keyboard.
- The **Keyboard** menu adapts PianoToLife to your keyboard:
  - **Standard** (default): works with every keyboard. Keyboards without release velocity
    send 0, 64 or 127 on every key release; PianoToLife reads every release as the calibrated
    normal release (the Note-Off Floor and Curve have no effect in this mode). Use **Release Decay** to
    make the release shorter or longer.
  - **Release Velocity 1-127**: for keyboards that measure how fast you release the keys
    (many Roland, Kawai, Kurzweil...) or behave in their own way. Their 1-127 range drives
    PianoToLife's dampers, release and key noise, fine-tuned with the **Keyboard Note-Off Curve**
    (above 32 = firmer releases). The **Keyboard Note-Off Floor** sets the value of the slowest
    release, so very low values, often sent by mistake, are read as a slow release, never an
    endless one. Check in the **MIDI Monitor**: your key releases should show
    many different values.
  - **Kawai VPC1**: made for the VPC1, whose release velocity stops around 100 and easily
    drops to 1 on a slightly slow release. Normal releases sound normal, slow ones stay
    natural. If it does not suit your playing, adjust the Keyboard Note-Off Floor and Curve or
    go back to Standard.
  - **N1X or others** (Yamaha N1X and similar Yamaha hybrids): these instruments report
    the key position through polyphonic aftertouch, only while the key comes back.
    PianoToLife measures the time the key takes to return and turns it into release
    velocity (no aftertouch at all = a very fast release). It can filter the aftertouch
    and CC19 messages so the hosted piano does not receive them.
  - **Yamaha P-525**: measures the timing of the release information the P-525 sends and
    turns it into release velocity.
  - In every mode but Standard, the release goes through the **Keyboard Note-Off Floor**
    (1 to 16, default 16) and the **Keyboard Note-Off Curve**, on PianoToLife's internal 0 to 64 scale
    (64 = a normal release; from a 1-127 keyboard, 64 and above = normal, as the MIDI rule says); PianoToLife's dampers, release and
    key noise use the result. **Note-Off to Host** chooses what the hosted piano gets: **Var**
    (the same value), **64** (always a normal release, no double treatment), **127**, or **Raw**
    (what the keyboard sent).
- **Silent Key** (list next to SYMPATHETIC RESONANCE): a silent key press lifts the damper
  without playing a note, so the string is free to resonate (play a chord over it, or hold it
  while lifting the pedal). **≤ 1** (default), **≤ 2**, **≤ 3** = notes at that velocity or lower;
  **Disklavier / N1** = polyphonic aftertouch 127 / 0, as sent by the Yamaha AvantGrand N1 and
  Disklavier XP (all velocities play in that mode); **Off** = none. The **MIDI Monitor** button
  shows, on the same line, what the keyboard sends, the release velocity PianoToLife's engine reads,
  and what is sent to the piano, with every difference highlighted.
- The speed at which you **lift your foot off the pedal** shapes the damping of all the
  strings in the same way.
  - **Progressive dampers** (always on): a light damper contact — a slow key or pedal
    release, or half-pedalling — silences the upper partials first while the fundamental
    lingers, like a real grand. A firm contact stops every partial together.
  - **Pedal Release Time** (default 80 ms): the fastest a released pedal can come back up. A
    pedal let go at once, or an on/off pedal, lands the dampers as if it took this long, so
    the sound does not stop abruptly; slower releases are measured as they are.

## Requirements

| | macOS | Windows |
|---|---|---|
| **System** | macOS 14 Sonoma or later | Windows 10 / 11, 64-bit (x64) |
| **Processor** | Apple Silicon (M2 or later recommended). Intel Macs are not supported. | Intel / AMD x64 (also runs on Windows on ARM through emulation) |
| **Formats** | Audio Unit, VST3, Standalone application | VST3, Standalone application (ASIO) |
| **Hosted piano** | Any AU or VST3 piano plug-in built for Apple Silicon | Any x64 VST3 piano plug-in, installed in `C:\Program Files\Common Files\VST3` |
| **Separation (stems)** | The Apple Silicon GPU (Metal) | A graphics card through Vulkan: an NVIDIA RTX with 8 GB of video memory or more recommended; AMD works; integrated Intel graphics are very slow |

### Separation speed (measured, November 2026)

One piece of 3 min 25 s:

| Computer | Stems FAST | Stems QUALITY | LYRICS |
|---|---|---|---|
| Mac mini M2 Pro (16 GB) | 48 s | 99 s | 8–9 s |
| Windows laptop, NVIDIA GeForce RTX 5050 Laptop (8 GB), Intel i7-13650HX | 22 s | 39 s | about 6 s |

Each piece is separated only once, then kept. A recent NVIDIA RTX card, even a laptop one, separates 2 to 2.5 times
faster than an M2 Pro; Macs with M5 or later have neural accelerators in their GPU (not measured yet). Without a
graphics card (the processor only), a piece can take 20 to 30 minutes. LYRICS: the first time, the Whisper model
(488 MB) is downloaded once, and on a PC the graphics card's driver prepares itself (a few seconds more).

**Help complete this table.** If you have a **Mac with Apple Silicon** (M1 to M6, any model) or a **PC with an NVIDIA
RTX card**, time a separation and send your result to pianotolife@outlook.com: your computer (Mac model and chip, or the
RTX card and its video memory), the length of the piece, and the FAST and QUALITY times (the first separation after a
start can take a few seconds more). Results from other computers are not needed: without an RTX card or Apple Silicon,
the separation is much slower.

On macOS, the plug-in does not load in a host running under Rosetta.

### macOS

1. Download `PianoToLife-<version>-macOS-AppleSilicon.pkg` from
   [Releases](../../releases/latest).
2. Double-click it. The installer is signed and notarized by Apple: no security warning.
3. Choose what to install: Audio Unit, VST3 and/or the standalone application.
4. In your DAW, insert **PianoToLife** as an instrument, then load your piano inside it
   with **Scan AU + VST3** / **Open AU or VST3**.

Optional integrity check:
```
shasum -a 256 PianoToLife-<version>-macOS-AppleSilicon.pkg
```
and compare with the `.sha256` file of the release.

### AU or VST3? (macOS)

Use PianoToLife in the **same format as your DAW**, and host a piano **in that same format**:

| You use | PianoToLife to insert | Pianos offered |
|---|---|---|
| Logic Pro, GarageBand, MainStage | **AU** | AU pianos |
| Cubase, Reaper, Studio One, Live… | **VST3** | VST3 pianos |
| Standalone app | — | AU and VST3 pianos |

- An older session or preset whose piano is in the other format reopens with its
  PianoToLife settings, but **without the piano**: just choose the piano again in the
  right format.
- Instruments that exist only as VST3 cannot be hosted in PianoToLife AU (and vice versa).
- In the standalone app, avoid switching from the VST3 to the AU of the same instrument:
  PianoToLife will offer to restart.

Tested on macOS in **Logic Pro and GarageBand (AU)** and **Reaper (VST3)**, with very good
performance in Reaper.

### Windows

1. Download `PianoToLife-<version>-Windows-Setup.exe` from [Releases](../../releases/latest)
   and run it: **Install for all users** (recommended: the VST3 goes to the standard folder
   every DAW scans) or **for me only** (no administrator rights: the VST3 goes to
   `%LOCALAPPDATA%\Programs\Common\VST3`; add this folder in your DAW if needed).
   Or download the `.zip` and copy the files yourself (steps 2 and 3).
2. **VST3 location:** PianoToLife only scans `C:\Program Files\Common Files\VST3`. Make sure
   your piano's VST3 is there (move it or re-run its installer if needed).
3. To use PianoToLife in a DAW, copy the **whole** `PianoToLife.vst3` folder to
   `C:\Program Files\Common Files\VST3`.
4. The `.exe` is not digitally signed yet: if Windows shows *"Windows protected your PC"*,
   click **More info → Run anyway**.
5. Standalone: **Options → Audio/MIDI Settings…**, choose **ASIO** and your audio
   interface's driver (or ASIO4ALL / FlexASIO), then **Scan VST3** and load your piano.

Tested in Ableton Live 12 (VST3).

## Setting up your piano (important)

PianoToLife provides the resonance and the sustain behaviour itself, and it listens to
the **dry** sound of your piano to drive the strings. So, **in the hosted piano**:

- **turn off** every *sympathetic resonance*, *string resonance*, *sustain resonance* or
  *pedal resonance* option;
- **turn off all reverb, effects and compression** (convolution rooms, ambience, EQ /
  "tone" effects, limiters, stereo wideners…). Otherwise the resonating strings would be
  fed with the room and the effects instead of the strings, and the calibration capture
  would measure them too;
- then follow the setup of your **pedal mode** below (sustain samples, key noise);
- set **Undamped Keys Above** to the last key with a damper on that piano (Steinway D: G6,
  Shigeru Kawai: A#6...), and with a Bösendorfer Imperial drag the left handle of
  **Sustain Free To** down to C0.

Need a room or some compression? Use **PianoToLife's own Piano Comp and Reverb**
instead: they are placed *after* the resonance engine, so the resonance stays clean and
the whole instrument goes through the same room. Any other effect can of course be
inserted after PianoToLife in your DAW.

Remember that the CPU load shown by your DAW for PianoToLife **includes the hosted piano**,
with its own settings and number of microphones.
On a slower computer, or if the CPU load is too high with the pedal down, try
**Enable Multicore Processing** first (same sound, the resonance is shared between cores), then
lower **Max Free Strings (CPU)**: fewer strings resonate at the same time, for a slightly
thinner halo.

#### About CPU meters

Each DAW measures the load differently, so the same work can look very different:

- **Activity Monitor (Mac)** shows the % of **one core** for each process (it can go above
  100 %); the **Windows Task Manager** shows by default the % of the **whole processor**. A plug-in
  computes on its track's audio thread, so its own work looks concentrated on one core while a
  multicore engine looks spread out. Compare the whole CPU, and above all listen for
  crackles.
- **Logic Pro** shows one bar **per core**, for the track played live with the small I/O
  buffer — the most demanding case. 50–60 % on one bar with the pedal down is normal and
  safe as long as there are no crackles. Helpful: a larger **I/O Buffer Size**,
  **Process Buffer Range: Large**, **Multithreading: Playback & Live Tracks**.
- **Reaper** shows by default an average over **all cores** (a few % can mean 30–40 % of
  one core), and computes tracks ahead of time. For a closer comparison, open
  **View → Performance Meter** (per-track and RT CPU).
- **Cubase** shows an average and a real-time **peak** (the peak behaves like Logic's
  bar); **ASIO-Guard** lowers the load of tracks that are not played live.
- **Ableton Live** shows the average time spent against the buffer; Live 12 can also show
  the load per track.

What matters is **no crackles and no overload message**. The heaviest case is playing
long glissandos with the pedal held down (hundreds of partials ringing at once). If you
hear crackles: raise the buffer size, try **Enable Multicore Processing**, then lower
**Max Free Strings (CPU)**.

### Pedal mode: Host Sustain, Host Sustain (stacked), Host Sustain (strict) or Pass-through?

**What are "sustain samples"?** Many sampled pianos contain two sets of recordings of
every note: one played with the pedal **up**, and one with the pedal **down**. The
pedal-down recordings include the sympathetic resonance of the whole instrument,
*frozen at the moment of the recording*. PianoToLife builds this resonance itself, live,
from the strings that are really free at each instant. If the piano also plays its
pedal-down samples, the resonance is there twice, and the frozen one does not follow
your pedalling.

The pedal section of PianoToLife shows what to turn off in the piano for the selected
mode.

**Pedal: Host Sustain (default) — recommended for most pianos.**
Some pianos give no way to turn off their sustain
effect or their pedal-down samples. Host Sustain keeps the pedal away from the piano: it
only plays its pedal-up (dry) samples, and PianoToLife holds the notes itself. Half
pedal, pedal catch, sostenuto and restriking are all included. A note struck again under the
pedal behaves like a hammer on a string that still vibrates: a **softer** strike rings over the
previous one (a loud note is never cut by a soft repeat), a strike **at least as loud** replaces
it. **Every strike gets its own Note Off** when the note is finally released,
so pianos that keep one voice per strike or count the keys never keep a note hanging.
It works with every piano tested (see **Tested pianos** below).
In the piano, turn off:
- **all Key Noise / release noise** (PianoToLife sends the Note Offs when the pedal comes
  up, so these noises would come at the wrong moment);
- its **sympathetic resonance / string resonance**, including pedal-up resonance.

With Host Sustain, half-pedalling keeps the piano's clean pedal-up sound while
PianoToLife's resonance fades progressively (treble dampers first). The result is a real
gradient, even with pianos whose own half pedal only switches between full samples.

**Pedal: Host Sustain (stacked).**
Same as Host Sustain, but every strike under the pedal rings over the previous ones, even a
louder one. For pianos that play a damper / release noise at each restrike. Set up the piano
exactly as for Host Sustain.

**Pedal: Host Sustain (strict).**
Same as Host Sustain, but every restrike under the pedal first gets the Note Off of the previous
strike, even a softer one. For scripted libraries that ignore a softer restrike of a note they still
hold. A softer restrike starts at the level the previous
strike still had (from its decay in the piano model), so the sound does not drop. Set up the piano
exactly as for Host Sustain.

Changing pedal mode (or una corda mode) lifts the pedals for everyone until you move the pedal again.

**Pedal: Pass-through.**
The piano receives your pedal and handles its own dampers, half-pedal and releases.
In the piano:
- turn off its **sustain samples** (pedal-down samples / "pedal resonance");
- turn off its **sympathetic resonance / string resonance**;
- **keep** its *half-pedal* and *repedalling* options.

Set **Half Pedal Damping Start / Full** to match your piano (defaults match our
reference concert grand).

### Tested pianos

| Piano | Pedal mode | Notes |
|---|---|---|
| **VSL Synchron Steinway D-274** | Host Sustain | Reference: default settings are tuned on it. VSL does not let you turn off its sustain samples. Turn off Key Noise, reverb and compression in VSL; use the **close mics** as much as possible. Keep **Ambience** at its **Default** with VSL's release at −inf: PianoToLife's release then carries the room the VSL release samples had. Confirmed on Mac and Windows (Intel Ultra 9 285H, 64-sample buffer). Example player presets: `PianoToLife-Example-Presets-VSL-D274.zip` in the latest release. |
| **VSL Synchron CFX** | Host Sustain | Works well ("they sound really good"). Key Noise off in VSL. |
| **VSL Synchron Concert D 1887** | Host Sustain | Works well with a captured SR model. |
| **VSL Synchron Imperial** | Host Sustain | Not tested yet — feedback welcome. Drag the left handle of Sustain Free To down to C0 to free its 9 extra bass strings. |
| **Kontakt pianos** (e.g. The Grandeur) | Host Sustain | Work well. Turn off Key Noise and the sympathetic / string resonance of the instrument. Pass-through also works if the instrument lets you turn off its sustain samples. |
| **Ivory 3** (Synthogy) | Host Sustain or Pass-through | Works in both modes. Turn off *Sympathetic Resonance* in the Ivory preset (and *Sustain* in Pass-through). To our ears the resonance and sustain even sound better than Ivory's built-in ones — a subjective opinion, not a promise. |
| **Session Keys** (Native Instruments, Kontakt) | Host Sustain (strict) | Its script ignores a softer restrike of a held note: use **Host Sustain (strict)**. Pass-through also works if you turn off its own pedal / resonance options. |
| **Galaxy Vintage D** (Kontakt) | Host Sustain | Works well; ANALYSE finds its 16 layers. Turn off its own resonance, pedal noises and reverb. |
| **Korg SX2 VST** | Host Sustain | Keeps one voice per strike; Host Sustain gives each strike its own Note Off, so restruck notes stop correctly. |
| **UVI Modern D** | Host Sustain | Works, and a restruck key no longer stays drawn down. **Keep Modern D's own release on and switch PianoToLife's Release Level off**: Modern D's release cannot be switched off cleanly (Off also cuts the note before its natural decay). Switch off Sustain and Sympathetic Resonance in Modern D and let PianoToLife play them. |
| **AcousticSamples C7** | — | "Flawless" (user report, Windows). |

Other VSL pianos: use **Host Sustain**, with Key Noise turned off in VSL.

## Enjoying PianoToLife? Donate

PianoToLife is free, and it took months of listening, measuring and comparing with real
pianos. If it has given your piano a new life, you can say thank you — the price of a
couple of coffees, **10 € or 20 €**, keeps the project moving:

<p align="center">
  <a href="https://www.paypal.com/paypalme/owfrappier"><b>♥ Donate to PianoToLife (PayPal)</b></a>
</p>

Every contribution, however small, is read, appreciated and turned into new versions.

## Naming your samples (AUTO NAME)

The key is found from the sound; the **layer** is safest from the name. AUTO NAME (on by default) uses it when every
layer of a key carries one of these, as a separate word: dynamics `Piano_C4_mp.wav` (ppp … fff), velocity range
`Piano_C4_033-064.wav`, velocity `Piano_C4_v64.wav`, layer number `Piano_C4_L3.wav`. Use one style for the whole
library; a note, a microphone (`mic2`) or a round robin (`rr2`) is never read as a layer.

## Distributing sampled pianos made with PianoToLife

Making sample sets with PianoToLife and playing them for your own use is free.
**Any public distribution of a sampled piano made for PianoToLife's sampler** (sample sets,
`.ptlset` / `.wptl` files, `[SAMP]` presets), **free or paid, requires my prior authorization.**
Please contact me at [pianotolife@outlook.com](mailto:pianotolife@outlook.com) before publishing anything: together we will set up its
protection (encrypted container, password) and the way it is distributed.

## Feedback

Found a piano that works (or doesn't)? Please open an
[issue](../../issues) with the piano name, its version, your pedal mode and your
PianoToLife settings.

## About

PianoToLife is developed by **Olivier Frappier**, pianist.
The code was designed and written with the help of **Claude** (Anthropic) and other AI
assistants, guided by many hours of listening tests and comparisons with real pianos.
Built with the JUCE framework. Photo in the Resonance drawer: Pexels, "Inside of a piano"
(Pexels licence).

The source code is not public; this repository hosts the official releases only.

---

<sub>
© 2026 Olivier Frappier. All rights reserved.<br>
Steinway, Vienna Symphonic Library / VSL, Synchron, Ivory / Synthogy, Kontakt / Native
Instruments, Korg, Yamaha CFX and Bösendorfer Imperial are trademarks
of their respective owners.
PianoToLife (formerly SympResHost) is an independent product and is not affiliated with, endorsed by or
sponsored by any of them. "Steinway D-274" designates the sampled instrument used for the
built-in resonance model.<br>
VST is a registered trademark of Steinberg Media Technologies GmbH.
Audio Unit and macOS are trademarks of Apple Inc.
</sub>
