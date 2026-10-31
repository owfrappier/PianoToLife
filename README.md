<h1 align="center">PianoToLife</h1>
<p align="center"><i>formerly SympResHost</i></p>
<p align="center"><b>Bring your VST / AU piano to life — and to realism.</b></p>
<p align="center">Replace your piano's static sympathetic resonance samples and canned pedal behaviour<br>
with one live, physically modelled string engine — from a single held key to every damper lifted.</p>
<p align="center"><b>New in 10:</b> no hosted piano needed — play your own samples with the built-in sampler.<br>Pedal-up samples are enough: resonance, pedals and noises are modelled live (hybrid sampling + modelling).</p>

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
  <img src="screenshot.png?v=1056" alt="PianoToLife interface" width="900">
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
  PianoToLife is free. <a href="https://www.paypal.com/paypalme/owfrappier"><b>♥ Donate with PayPal</b></a> to support its development.
</p>

<p align="center">
  <a href="https://www.youtube.com/watch?v=aNzbEqNP4QE">
    <img src="https://img.youtube.com/vi/aNzbEqNP4QE/maxresdefault.jpg" alt="Video: 4 sampled pianos through PianoToLife" width="640">
  </a><br>
  <b>▶ Video: 4 sampled pianos through PianoToLife</b> (VSL D-274, a second commercial grand, a 3-layer Steinway B, VSL 1887) — which one do you prefer?
</p>

---

## What's new in 10.5.6

**AUTO DYN places every key, and the SAMPLER EDIT tools in the order to use them.**

- **AUTO DYN listens to every key** and places its layers on the reference curve (Grand D / Grand B / Upright),
  whatever its number of layers, then smooths the boundaries with the neighbouring keys and levels them. Libraries
  with uneven velocities from key to key, manually sampled pianos, or a layer missing in a register now play evenly
  along the keyboard. A4 stays the anchor; key gains (BALANCE) are kept. The AUTO DYN curve is now shown relative
  (0 dB = A4 at v127).
- **SAMPLER EDIT**: the tools are in the order to use them, with > between them: FILL GAPS > ALIGN ATTACKS >
  AUTO DYN > FIX STEPS > AUTO COLOR > BALANCE > AUTO RELEASE.
- The listening part **Pedal FX** is now called **Half/rel/catch Pedal**.
- **Pedal catch**: with the pedal fully up for more than 220 ms (was 300 ms), the caught strings are now really
  damped - closer to the reference piano. Quick pedal changes are unchanged.

Manuals updated for 10.5.6: [User Manual](USER_MANUAL.md) · [Manuel d'utilisation](MANUEL.md) ·
[Sampler Manual](SAMPLER_MANUAL.md) · [Manuel du sampler](MANUEL_SAMPLER.md).

### Also in 10.5.4

**Fix: unorthodox MIDI file endings (BOUNCE / PLAY / REC).** A file ending with notes still held now rings out to
the end instead of being cut.

### Also in 10.5.3

**The HOST pedal without Release, and a listening selector you can combine.**

- **HOST mode: half pedal and late pedal catch now work even with Release Level off.** The pedal keeps its own
  strings: no release sound, but notes held by a half-lifted pedal and notes caught late by the pedal still ring as
  they should, for about the same CPU. With Ambience on, these strings also feed the room.
- **Listening selector**: *Full Piano = Piano Only + Half/rel/catch Pedal + Symp Res + Release + Noises + Ambience*. Light one or
  several parts to hear only them - they add up; with none lit you hear the full piano. The selection is kept in the
  preset / session. (Release includes Felt-Contact; Noises = Key Noise and Pedal Noise.) The old right-click menu is
  gone.
- Release Level tooltip: in HOST mode the pedal keeps its strings even when Release is off.


### Also in 10.5.2

**Three automatic tools - the right resonance level, the right colour, the softest velocities put to use - and a truer half pedal in HOST mode.**

- **AUTO CAL** (next to Resonance Level): PianoToLife holds A3 silently, plays A4 once and measures how loud the
  resonance is compared with the piano's own sound. Resonance Level 0 dB is then calibrated on the piano and the
  resonance model you use: the same balance as the reference, whatever the piano, its volume, the sample set level or
  the model. **If your recaptured .srpiano or your sample sets sounded too weak in resonance, run AUTO CAL once.**
  - Takes about 3 s; don't play meanwhile. Resonance Level still turns it up or down around it.
  - HOST and SAMPLER each keep their own calibration, saved in the preset / session; DEFAULT puts them back to 0.
  - The button is lit while a calibration is in use; its value is shown on the Piano Model line.
  - After a capture, PianoToLife offers to run it on the new model. Pedal Noise keeps its own level.
- **AUTO COLOR** (SAMPLER EDIT): sets SOFT COLOR and HARD COLOR so that your layers open up from soft to loud like the
  reference piano (brightness measured on A2, A3, A4, A5 at 13 velocities). Only the shape counts: a piano keeps its
  own character, brighter or darker. Run it last: AUTO DYN, FIX STEPS, AUTO COLOR. UNDO puts the sliders back.
- **AUTO DYN uses the softest velocities**: pp layers recorded softer than the reference ever plays are no longer piled
  at v1-v8 - they are spread from v1 up to the first layer above v16, their levels set on the reference curve.
  Libraries with very soft layers (and even the most detailed ones) gain real, playable pianissimos.
- AUTO DYN now listens to the layers with SOFT / HARD COLOR, as they are played.
- **Half pedal in HOST mode**: a note held by a half-lifted pedal now dies away like the real note in its first
  seconds (it rang on far too long at mid pedal). HOST and SAMPLER now behave alike from CC 61 to 75.
- The built-in resonance model is labelled **default V9** (its data have been V9 since 10.3.6; only the label still
  said V8).


### Also in 10.4.6

**AUTO DYN for libraries normalised by loudness, the Samples menu back, the velocity in SHOW BY MIDI.**

- **AUTO DYN follows the Samples setting** (next to AUTO LAYERS): Normalised = the layers placed by their timbre,
  Not normalised = by their levels. On **auto** it now also recognises a library normalised by loudness (layers of A4
  less than 12 dB apart), whose layers were all piled at the top; libraries with few layers are often placed more
  precisely too.
- SAMPLER EDIT: the **Samples** menu (auto / Normalised / Not normalised) is back, next to AUTO LAYERS; the reference
  menu shows "Grand B" in full again.
- SAMPLER EDIT: with **SHOW BY MIDI**, the velocity you play is shown next to the number of layers.

### Also in 10.4.4

**AUTO DYN: smooth and light on large libraries.**

- **AUTO DYN reads only the beginning of each sample** — what it listens to — instead of the whole file. On a library
  with many velocity layers it no longer goes through gigabytes of memory: the progress bar moves smoothly, and the
  piano plays cleanly afterwards without restarting PianoToLife.
- **SAMPLER EDIT is faster on large sets**: the timbre of the layers (SOFT / HARD TIMBRE, the coloured layer
  boundaries) is computed much faster when the set changes.

### Also in 10.4.3

**AUTO DYN fixed on Windows, CLEAR ALL, SHOW BY MIDI.**

- **AUTO DYN no longer crashes on Windows** (standalone and VST3): it now works on large libraries too.
- SAMPLER EDIT: **CLEAR ALL** (left of DELETE) empties the whole set — every key, every microphone — after a warning
  that gives the number of samples. UNDO brings it back; your files are not touched.
- SAMPLER EDIT: **SELECT BY MIDI is now SHOW BY MIDI**. The key you play is shown in the side panel, with a red line
  in the zone that sounded, but **the selection no longer changes**. ALIGN ATTACKS, BALANCE, FIX STEPS and AUTO
  RELEASE work on the zones you selected, or on every key when nothing is selected (click an empty part of the grid
  to clear a selection). AUTO DYN always works on every key.

### Also in 10.4.2

**Two EQs, a metronome, MIDI playlists, PANIC and a richer Compact view.**

- **EQ1 / EQ2** — click **EQ** under REVERB: **EQ1** works before COMP and REVERB (the tone of the piano), **EQ2** after
  them, before the Ceiling (to hear your **headphones flat**). Draw on the curve (double-click = a point, drag =
  frequency / gain, mouse wheel = Q, right-click = remove), PREAMP, RESET — or **LOAD** a headphone preset: a
  `ParametricEQ.txt` from AutoEq (oratory1990 measurements) or an Equalizer APO file. Kept in the preset and the session.
- **METRO** (standalone): 30–360 BPM with TAP, every usual bar (1/1 … 12/8) with accents, wood or beep, volume and a
  count-in. Heard only — never in a bounce. With the metronome on, REC starts on a bar and the MIDI file carries the
  tempo and time signature, so the take sits on the grid of a DAW.
- **MIDI playlists**: LOAD MIDI takes several files, a folder or an **.m3u** list; previous / next, the pieces follow
  one another, loop, save the list.
- **PANIC** (next to Silent Key): stops everything that sounds — stuck notes, resonance, sampler, room, player,
  metronome — and sends All Notes Off / All Sound Off to the hosted piano.
- **Compact view**: now with the MIDI player and METRO, the chord, a lit and clickable keyboard, TRUE PEAK and LUFS.
- The keyboard of DAMPER MECHANICS is taller, with the proportions of a real keyboard.
- SAMPLER EDIT: the number of layers of the key is shown; **RECAL A4 is now called AUTO DYN**.

### Also in 10.4.0

**See what you play: the chord name and a lit keyboard.**

- **The chord you play**, in large letters left of BODY (DAMPER MECHANICS): the keys held and the notes the pedals
  keep ringing. Only chord names (C, Am7, Cmaj7/E, G13…), never a list of notes. A chord held in the left hand stays
  shown under a right-hand melody, and is completed when the melody adds to it. Read from MIDI: no CPU cost.
- **An 88-key keyboard** under the strings lights up with them; its colour follows the velocity (pale = soft, full
  orange = loud), paler for the notes kept by the pedal. **Click it to play** — lower on the key = louder, drag for a
  glissando — in HOST and SAMPLER, through the same path as your keyboard (MIDI Monitor, ENGINE MIDI REC).
- The dampers sit a little higher to make room.
- **EDIT at 90 % / 80 %**: the window is now scaled as a whole; no more cut buttons.

### Also in 10.3.8

**SAMPLER EDIT: more libraries mapped right, a handier sample list.**

- **The sample list** (side panel): click a sample to select it (highlighted); leave the mouse on it to see its
  information (file, audio format, key, velocities, gain, level, brightness, tuning, strike); **right-click to hear it
  alone** (right-click again = stop; it works in the grid too). A long list scrolls (mouse wheel, ▲ / ▼) and follows
  the selection.
- **In EDIT you hear the microphone you are editing**, alone and neutral (0 dB, centred, full width, no delay, no L↔R,
  BODY at 0), whatever the MIX. Back to the main window, the MIX drives the microphones again.
- **AUTO LAYERS: Samples auto / Normalised / Not normalised.** A library that keeps its dynamics is now ordered and
  placed by the **levels** of its layers: its brightness can mislead (the softest layers carry more hammer and
  mechanical noise and measure "brighter" than a mezzo forte). Normalised libraries are still placed by brightness.
  Auto decides key by key (layers more than 12 dB apart = not normalised).
- **AUTO NAME reads more file names:** a velocity right after the note (`Piano-A2-40`, `NP60-103`); a MIDI key glued
  after letters (`NP60`); a number that follows the loudness of the layers in either direction (a take or hammer-time
  number); names one or two octaves off for the whole library (A0 named `A-2`) are corrected on import. With AUTO LAYERS
  off, velocities ending at 127 are read as the top of each layer.
- **AUTO KEY:** very soft treble notes (C8, B7…) no longer land in the bass — up there the hammer noise outlasts the
  string; PianoToLife now also listens to their first 150 ms above 1.5 kHz.
- **Undamped Keys Above** is also in the EDIT key panel (the same setting as the main window). In SAMPLER, keys on
  release Auto above it have no damper, as on a real piano; moved by hand, the keys that cross it get AUTO RELEASE.
  Sets on release Auto: the keys above G6 (default) now ring without damper.

### Also in 10.3.7

**MIDI monitoring and the MIDI player / recorder, redesigned: more consistent, simpler.**

- **The recorder writes what PianoToLife plays** (ENGINE MIDI REC, under Disable CC19, on by default): every Note Off
  carries the release as our engine reads it — the slow releases of an N1X, P-525 or VPC1 included (64 = a normal
  release, lower = slower) — with the velocity curve applied. All the aftertouch is kept (the N1 / N1X release and
  silent keys), so the files stay Disklavier / N1 compatible and replay the same in any DAW or piano. Off = the raw
  keyboard input, as before.
- **One rule:** Disable Aftertouch and Disable CC19 only keep these messages away from the hosted piano; PianoToLife's
  engine and the recorder always see them.
- **MIDI Monitor:** the Engine column also shows the aftertouch and CC19 the engine reads.
- **Simpler recording:** after REC, the take starts on your first note or pedal (no silence at the start; pedals
  already down are kept). Click REC again and the save window opens — no more SAVE MIDI button. PLAY plays the take
  at once, without LOAD MIDI. LOAD MIDI and the save open the same folder.

### Also in 10.3.6

**Important fix — stereo phase.** BALANCE (the key gains of the sample mapping) and the brightness used by SOFT /
HARD TIMBRE, FIX STEPS and AUTO KEY were measured on L + R. With two spaced microphones a key can be out of phase
between the channels: it lost several dB and some partials in that sum, so BALANCE boosted it too much (A5 of a
Steinway B: +6 dB, too loud by ear). **Every analysis is now made in stereo**, channel by channel. Sets made before are
measured again in the background when they are opened (SAVE SET keeps it, then it is never done again).

**Piano Model capture in stereo, new default model.** The capture of a Piano Model (.srpiano), in HOST and SAMPLER,
now looks for the partials of every note in both channels: the partials out of phase between the microphones are no
longer lost. Capture again the pianos recorded with spaced microphones. The built-in model (concert grand) was
captured again this way (70 more partials, mostly in the bass), at the same resonance level as before.

**Kontakt .ncw samples** (SAMPLER, EDIT): drop the `.ncw` files of a Kontakt library (not encrypted) like WAV files;
they are rewritten as WAV or FLAC when the set is saved. Use only libraries whose licence allows it; encrypted
libraries are not read.

**Drop a whole folder** in EDIT: its samples and those of its sub-folders are imported, without the files whose name
says they are not a pedal-up note (releases, noises, pedal down, una corda) — PianoToLife models those itself.
**Round robins** in the names (`rr2`, `seq2`, or `..._Dyn1_..._21_02`) are left out after the first: REP gives every
strike its own variation. A key written `109` is read as C8.

**L↔R** in MIX: mirrors the stereo image of a microphone (the pianist's or the audience's view).

Also: no more spinning wheel when switching from HOST to SAMPLER with a set made before 10.3.5.


### Also in 10.3.4

**Colour between velocities, much improved** (SAMPLER). SOFT TIMBRE and HARD TIMBRE now follow the colour of the
reference piano (Grand D, Grand B or Upright), measured on every key at every velocity: from the velocity a sample was
recorded at to the velocity you play, the strike gets darker or brighter as the reference does — about twice as much
in the 4–8 kHz range as in 2–4 kHz, up to +18 dB. Even a set with only 3 velocity layers now sounds like a real strike
at every velocity in between, and the layer boundaries disappear.

**REP — Real piano repetition** (below CAL: Off / Grand D / Grand B / Upright). On a real piano no two strikes sound
exactly alike; a sampled piano replays the same recording every time — the "machine-gun" effect of repeated notes.
The old cure of sample libraries is **round robin**: several recordings of every note at every velocity, played in
turn — heavy, and rarely complete. REP simulates the repetition of a real piano instead, with the strike-to-strike
differences measured on the reference. In SAMPLER, each strike gets its own small differences of level, brightness,
decay and attack, a tiny detune in the bass, and a key struck again while it still sounds builds up naturally:
**large round-robin sample sets are no longer needed**. In HOST, only the velocity varies slightly (never out of its
velocity layer). Off by default; saved in presets and sessions (older ones open with REP Off).

**Piano Model capture in minutes in SAMPLER.** Capture now reads your samples directly, offline, at the centres of
your layers: a few minutes instead of a real-time recording. A window lets you tick the microphones of the model
(MIC 1 by default; close microphones are recommended — the room microphones put the hall into the string decays).


### Also in 10.3.2

**BALANCE: an even volume from one key to the next** (SAMPLER, EDIT). A piano sampled by hand is never struck with
exactly the same force on every key, so some notes stick out. BALANCE measures every key at velocity 127 and brings
it onto a smooth curve with the key's gain (at most 6 dB), all its layers following: **Smooth** keeps your
recording's own balance from bass to treble and only removes the jumps; **Grand D**, **Grand B** and **Upright**
follow the bass-to-treble balance of a reference piano. Velocity ranges, layer gains and dynamics are not touched;
one UNDO.

<p align="center">
  <img src="screenshot1b.png?v=1056" alt="SAMPLER EDIT: a Steinway B sampled by hand with 3 velocity layers" width="900"><br>
  <i>A Steinway B sampled by hand with only 3 velocity layers: placed on the Grand B reference, joined by SOFT and
  HARD TIMBRE (green boundaries), and evened out key by key with BALANCE.</i>
</p>

**User manuals, in English and French.** A general manual (how the modelling works in HOST and SAMPLER, and why the
sampler only needs pedal-up samples) and a sampler manual (from a folder of samples to a playable piano, every
button explained): [User Manual](USER_MANUAL.md) · [Manuel d'utilisation](MANUEL.md) ·
[Sampler Manual](SAMPLER_MANUAL.md) · [Manuel du sampler](MANUEL_SAMPLER.md).

### Also in 10.3.1

**Clearer release (Note Off) handling, one chain for every keyboard.** How fast you let a key come up now goes
through a single, visible path. Two settings shape it for all keyboards that send a release: **Keyboard Note-Off
Floor** (1 to 16, the value of your slowest release, so a very slow release can never ring on endlessly) and the
**Keyboard Note-Off Curve**. The old Note-Off Velocity Curve is gone: no more two curves stacked on each other. PianoToLife's engine works internally on a 0 to 64 scale (64 = a normal release), whatever your keyboard sends
(0 to 127): following the MIDI rule, 64 and above is a normal release, lower values are slower releases.

**Choose what the hosted piano receives.** The new **Note-Off to Host** menu separates the release velocity used by
PianoToLife's own engine from the one sent to your piano: **Var** (the same value for both), **64** (always a normal
release: PianoToLife alone handles slow releases, no double treatment), **127**, or **Raw** (exactly what your keyboard
sent). PianoToLife's engine always uses the shaped value.

**Yamaha N1X, P-525 and other release-sensitive keyboards.** Keyboards that measure the release through aftertouch
(N1X and similar Yamaha hybrids) or through their own timing (P-525), as well as keyboards that send a real Note-Off
velocity (Release Velocity 1-127, Kawai VPC1), all go through the same Floor and Curve.

**MIDI Monitor in three columns.** On the same line: what your **Keyboard** sends, the release velocity PianoToLife's
**Engine** reads (with the measured release time on an N1X or P-525), and what goes to the **Host**. Any difference
is highlighted, and the export uses the three columns too.

Your keyboard has its own way of sending releases? Please contact me with an explanation of the MIDI it sends (a MIDI
Monitor export is perfect), and I will look at supporting it.

### Also in 10.3.0

**A much stronger streaming engine for large pianos.** The sampler now reads its samples from the disk with several
threads, and every voice reads its own file in order (no more jumping back and forth when several notes play the same
FLAC sample). On the same heavy test (sustain pedal down, notes everywhere), the busiest disk thread went from 90 % to
20 % of its time: far more headroom for deep libraries, slower disks and dense playing.

**Fast loading, even for huge sets.** The beginnings of the samples are read by several cores at once, and a hidden
slowdown that grew very fast with the number of samples is gone: a 5,192-sample piano (87 GB of WAV, 7 GB once in
FLAC) that froze the window for minutes now loads quickly, with a progress bar.

**Cleaner voice management.** When the polyphony is reached, the quietest voice no longer cuts off with a click: it
fades out in 8 ms while the new note takes a spare voice.

**Missing samples handled.** When a session or the last state points to a piano whose samples were deleted, moved,
or are on a disk that is not connected, a clear window asks to LOCATE them or to FORGET that piano (it is then no
longer asked about).

**Progress bars everywhere.** Importing, SAVE SET (encoding, then writing), loading a set or a session, ALIGN ATTACKS,
RECAL A4 and a new Preload in MIX all show a clear progress bar, in EDIT and on the main window.

### Also in 10.2.0

**Import your .sfz and Decent Sampler (.dspreset) pianos.** Drop the file in EDIT: its mapping is taken as written
(keys, key ranges, velocity layers, level, tuning, start) on the displayed microphone. What PianoToLife models itself
is left out: release samples, pedal-down samples, pedal noises and round robins. A Decent Sampler piano with several
microphone groups goes to MIC 1, MIC 2... in order. WAV, AIFF and FLAC samples can still be dropped as before.

**It repairs what the library got wrong.** Many free libraries are badly programmed. PianoToLife now detects a mapping
written one octave off from the sound of the samples and moves it back, plays strikes that come up to 1.5 s late on time
after ALIGN ATTACKS, and switches FADE IN on for samples whose start was cut inside the sound.

**FLAC in your sample files** (FLAC switch in EDIT): the samples of a set are stored without any loss, identical to the
bit, and piano samples shrink a lot (one 11 GB set became 1 GB). Less to read from the disk, no added latency. Samples
above 48 kHz are converted to 44.1 / 48 kHz (a piano has nothing useful above 20 kHz).

Also: a progress bar while importing (click the status line to stop; nothing changes before the end), large libraries
no longer fill the memory while they are analysed, and RECAL A4 works when A4 has no sample of its own.

### Also in 10.1.9

**Interface fixes, mainly for second screens.** The hosted piano's window, MIX, the MIDI monitor and every dialog now
stay on PianoToLife's screen. They could end up on another screen (a virtual or switched-off display) and seem lost,
and a hidden dialog could block the whole interface. They now come back on their own when a screen is added or removed.

**MIX window (SAMPLER):** the microphone names, ON / OFF and the streaming and voice settings are always shown, presets
from earlier versions included; an off microphone reads OFF. New defaults: SSD, Preload Auto, cache 128 MB, 256 voices.

### Also in 10.1.8

**Piano Models at the same resonance level.** A captured Piano Model (.srpiano) was levelled on the piano's loudest
strike, so a piano with sharp attacks got a weaker resonance and had to be compensated by hand. Now every model is
matched to the same resonance level when it is loaded, your existing captures included (the gain is shown after the
model's name). Each piano keeps its own character: its balance between bass and middle and its decay times.

**LEVEL TEST** (next to Capture): plays A0, C2, C4, C6 and C8 at velocity 127 and tells you the loudest strike and
whether the piano clips, before a capture or a concert. The capture's saturation warning now reports real clipping only.

**BODY on the main window, for HOST too** (left of the SOFT pedal): the perceived size of the piano, now also on a
hosted piano, with no latency.

Also: stereo meters per microphone in MIX, the limiter's meter (LIM) under CEILING, **FADE IN** option in EDIT (a 1 ms
fade at the start of every sample), with AUTO LAYERS off the velocity ranges written in the file names (`033-064`)
are applied exactly, and on Windows a preset double-clicked while PianoToLife is open goes to the open window.

### Also in 10.1.6

**A piano is now two files: its preset and its samples.** A `[SAMP]` preset carries its mapping and its resonance
model; only the samples (`.wptl`) stay apart. Double-click a preset (standalone) or drop it on the PianoToLife window
(plug-in too): it loads at once and joins your preset list. Its `.wptl` is found beside it, in your library or where it
was; if not, PianoToLife asks where it is (as Kontakt does) and remembers it. Presets are also saved beside their
`.wptl`, so a piano's folder is complete to move or to send.

**AUTO KEY:** the extreme treble of far microphones is now placed right (soft F#7..C8 used to land octaves low), and
note names in small letters are read (`pp_f#7`, `c8`). Tip: put the note in the file name as a separate word (`C4`,
`F#7`, `Bb3`, `f#7` or `060`) and every sample lands on its key, with or without AUTO KEY.

Also: **Delete password** in EDIT > PASSWORD, and **pianos for sale**: a sample set can be protected and opened only
with a licence in the buyer's name (contact me if you publish sampled pianos).

### Also in 10.1.5

**ALIGN ATTACKS now aligns every microphone.** Each sample of each microphone starts 3 ms before its own strike.
Badly cut libraries (strikes up to 15 ms late, microphones cut separately) now play tight and in phase: no more clicks
on the distant microphones, steady timing across the velocity layers. Run ALIGN ATTACKS again on your sets to get it.

Also: RENAME and SAVE use the name of the set's file (no more "My piano").

### Also in 10.1.4

**Important fix — repeated notes in SAMPLER mode**, keys up and under the sustain pedal: a new strike no longer cuts
the previous one; it goes on, a little lower, as on a real piano (up to 4 voices per key, "Per key" in MIX).

Also: **AUTO NAME** reads more naming styles (see *Naming your samples*), **RENAME** of a set in EDIT, and a red
**velocity line** with SELECT BY MIDI.

### Also in 10.1.2

**This update is mainly for the SAMPLER.** Its automatic functions were made much stronger, above all for **misleading, normalised sample libraries** — where every layer was raised to the same peak, so that an ff can measure quieter than a pp. PianoToLife no longer trusts the levels of such samples: it **looks at each strike's attack and brightness** (its timbre) to know how hard it was played, then rebuilds the real dynamics. HOST mode is unchanged.

- **AUTO KEY** is now right in the extreme treble too (a soft, strongly stretched C8 / A#7 used to land two octaves low).
- **RECAL A4 understands normalised samples**: it reads the attack and brightness of each layer instead of its level, places the layers by their timbre and rebuilds the real levels (see below).
- **AUTO NAME** (on by default): when the file names carry the dynamics (pp, p, mp, mf, f, ff...), they set the order of the layers — no more inverted layers when two dynamics sound alike (an f as bright as its ff). Switching it on puts every key back in order at once.
- **COLOR of SOFT / HARD TIMBRE** now acts on every note: up to a strike 24 velocities softer (more felted) or brighter, even at a layer's own velocity.
- **NEW**: start an empty set in one click (no sample, no password).
- **SAVE AS VARIANT**: several sets (.ptlset) on the same protected samples (.wptl), without copying them.
- **STRETCH**: a sample can also play the keys around it (transposed) — **FILL GAPS** completes a library sampled every 2 or 3 notes in one click; by hand, Cmd / Ctrl + drag.

### Auto-mapping that copes with real-world libraries
Mapping a sampled piano by hand takes days. PianoToLife does it in minutes, by **listening** to your samples rather than trusting their names or levels:
- **AUTO KEY** finds each sample's key from its sound — down to the stretched, fast-decaying top octave (a soft C8 tuned +70 cents is still a C8), whatever the file names say.
- **AUTO LAYERS** and **RECAL A4** place the velocity layers on the dynamics of a real grand: RECAL listens to A4, puts every layer where its loudness belongs, levels it, then sets every key the same way.
- **Normalised libraries are handled**: when every layer was normalised to the same peak (the real loudness is gone — an ff can even measure quieter than a pp), PianoToLife notices it and stops trusting the levels: it reads the **attack and the brightness** of each strike, places the layers by that timbre and rebuilds their real levels from the reference curve.
- **SOFT TIMBRE / HARD TIMBRE** and **FIX STEPS** then join the layers so smoothly that the boundary map turns green: a 3- to 6-layer library plays like a deeply sampled piano.

### Also in 10.1.0 — the built-in sampler

PianoToLife can now **play your own piano samples**, without a hosted piano. Switch **HOST / SAMPLER** at the top of the window: in SAMPLER, the hosted piano is set aside and PianoToLife's own sampler plays, with all of PianoToLife's engines on it (sympathetic resonance, release, una corda, pedals).

- **Your samples, a few clicks**: load your WAV / AIFF samples in **EDIT** (Kontakt-style key / velocity map). **AUTO KEY** finds each sample's note, **AUTO LAYERS** builds the velocity layers, **RECAL A4** measures the tuning and the loudness of your layers by listening to them. Fine edits per key: tune, gain, low-pass, envelope; **SELECT BY MIDI**, **UNDO / REDO**.
- **Smooth dynamics even with few layers**: **SOFT TIMBRE** gives the notes softer than a layer the spectrum of a softer strike, **HARD TIMBRE** (option) brightens the strikes above it. A map shows the step at every layer boundary (green / orange / red) and **FIX STEPS** evens it out, smoothed between neighbouring keys (one UNDO). A 3-layer Steinway B now plays like a deeply sampled piano.
- **Attacks aligned (ALIGN ATTACKS)**: after the mapping, one click finds the strike in every sample and makes every strike of the whole keyboard come 3 ms after the key is played, whatever the layer — no more flutter when the dynamics change, no flam on repeated notes. Every microphone is aligned on its own strike too (10.1.5): in phase, no clicks; the files are not changed; one UNDO.
- **COLOR of SOFT TIMBRE and HARD TIMBRE**: how much darker the soft strikes and how much brighter the loud ones, for the whole set (-100 % to +100 %, 0 = as measured).
- **A real piano release**: **AUTO RELEASE** sets each key's damper time by register; the release velocity counts (a slow key release lands the damper later and softer); keys without dampers ring on.
- **A native half pedal**: under a half pedal the released notes are damped by the samples themselves, continuously, with the two-part decay of a real damper (fast part + long residue); re-pedalling keeps the level reached.
- **A native una corda**: each voice keeps the velocity played and gets the una corda measured on the real una corda samples of a concert grand (level and partials, per register and velocity), plus the halo of the string not struck.
- **Sustain: Progressive / Switch**: for keyboards whose pedal should act as on / off (Switch: 64 and above = down). Progressive (the half pedal) stays the default. SAMPLER always uses Host Sustain and Una Corda Simu (both greyed there; your HOST choices are kept). Sostenuto works.
- **Large sets stream from the disk** (DFD): only the beginning of each sample stays in memory. Choose the preload, the cache and the polyphony (60…256, Max 512) in **MIX**; a disk test tells you if your drive is fast enough.
- **Microphones**: **MIX** mixes up to 5 microphone positions (level, pan, width, delay, meters); a microphone switched off is not loaded.
- **BODY** (main window, left of SOFT; was in MIX before 10.1.7): the perceived size of the piano — every note's own fundamental raised or lowered, fully in the bass and the middle, fading out in the treble.
- **TRUE PEAK** (MIX): per microphone and for all 5 together, 4 x oversampled; red as soon as it clipped, until you reset it.
- **Protected sets**: every save hides the samples in an encrypted container (`.wptl`), rewritten only when samples change. A password protects **EDIT**, never playing. A set saved on Mac opens on Windows and back.
- **Presets**: SAMPLER presets are marked `[SAMP]` and kept in `Presets/Sampler`; the preset list follows the mode.
- **Tuning**: SR Transpose, SR Fine Pitch and SR A4 Tuning play on the sampler; the A4 measured by RECAL is sent to SR A4 Tuning, so 440 Hz plays the set as recorded.

HOST mode is unchanged: everything from 9.5.3 is there.

### Also in 9.5.3

<table>
<tr><td>🎯 <b>Automatic velocity calibration</b></td><td>In the Velocity panel, click <b>ANALYSE</b>: PianoToLife plays A4 to your piano at the 127 velocities (about 1 min 20 s), finds its real layers and their levels, then proposes a velocity curve calibrated for <i>your</i> piano (<b>Apply</b> / <b>Keep my curve</b>). The CAL button is gone. Before ANALYSE, set the piano's own velocity curve to <b>linear</b> and its dynamics to <b>100 %</b>.</td></tr>
<tr><td>🎹 <b>The dynamics of a real piano</b></td><td>Choose the curve in the list: <b>Even</b> (each velocity the same step louder), <b>Grand D</b> (concert grand, Steinway D type), <b>Grand B</b> (grand, Steinway B type) or <b>Upright</b> (Yamaha U4 type). These come from the loudness of A4 measured on real piano models, stretched onto your piano's own range from softest to loudest; no real layer is skipped. Choosing a curve applies it at once. Many VST pianos are played with a much wider range than a real piano has (ppp that no real piano makes): the calibration brings back a natural touch.</td></tr>
<tr><td>🎛 <b>CURVE adapts it to your keyboard</b></td><td>The CURVE knob no longer replaces the curve: it bends what you play before it. Right = louder with less effort (heavy keyboard), left = you must play harder (light keyboard). The calibrated or hand-drawn points stay; the preview shows the points (dim line) and what really plays (bright line). Older sessions open with the same touch.</td></tr>
<tr><td>⚠️ <b>Clear warnings</b></td><td>If the piano varies or blends its samples (Smear, round robin, humanize, velocity or timbre variation), or if too many layers are found, PianoToLife tells you what to switch off instead of calibrating wrongly. With VSL Synchron Pianos, set <b>Smear off</b> before ANALYSE.</td></tr>
<tr><td>🛡 <b>Anti-crash on preset loading</b></td><td>When a hosted VST3 / AU could not load its preset or settings (missing or corrupted files, e.g. Kontakt 7), previous versions could crash, and crash again on every relaunch. Now the piano shows its own warning and PianoToLife goes on loading.</td></tr>
</table>

### Also in 9.5.2

<table>
<tr><td>🎚 <b>CAL: a velocity curve made for your piano</b></td><td>In the Velocity panel, click <b>ANALYSE</b> (the layer detector, formerly LAYERS), then <b>CAL</b>: PianoToLife writes a velocity curve with even loudness steps, from the softest to the loudest sound of <i>your</i> piano, without skipping any of its real layers. On the VSL Steinway it matches the curve we had tuned by ear for hours. CAL stays greyed out until the layers of the hosted piano are known.</td></tr>
<tr><td>📊 <b>Your piano's layers on the curve</b></td><td>The real velocity layers are drawn on the left of the velocity curve, with light lines across. A layer your curve never reaches turns <b>orange</b>, and the tooltip lists them.</td></tr>
<tr><td>🎙 <b>Faster, cleaner capture (about 35 min)</b></td><td>The capture now starts by finding the piano's real layers on A4, then strikes each velocity in the middle of a layer, never in a crossfade. Held notes stop as soon as nothing more can be measured (the treble no longer waits 20 s): about 35 minutes instead of 45, same model. Before capturing, set the piano's own <b>velocity curve to linear</b>.</td></tr>
<tr><td>🎹 <b>New built-in Steinway D-274 model (V8)</b></td><td>Captured again with the Synchron velocity curve linear: 60 layers found on A4, 1730 partials.</td></tr>
<tr><td>🦶 <b>Pedal: Host Sustain (strict)</b></td><td>For scripted libraries that ignore a softer restrike of a note they still hold, such as <b>Native Instruments Session Keys</b>: every restrike first releases the previous one, and a softer restrike starts at the level the previous note still had, so the sound never drops. To our ears, Session Keys sounds even better this way than with its own pedal (Pass-through).</td></tr>
<tr><td>🔄 <b>Changing pedal mode = pedals up</b></td><td>Switching between Pass-through and Host Sustain, or between una corda BP and Simu, now lifts the pedals for everyone (the piano and PianoToLife) until you move the pedal again. No more notes left hanging or a pedal stuck down after a switch.</td></tr>
<tr><td>🚨 <b>"HOSTED PIANO CLIPPING!"</b></td><td>If the hosted piano itself clips (its own output reaches 0 dBFS or is flattened), PianoToLife shows it in red in place of TRUE PEAK MAX: lower the volume in the piano, then raise the level in PianoToLife if needed.</td></tr>
<tr><td>🖥 <b>Standalone: safer audio</b></td><td>On first launch the buffer is never under 64 samples, the sample rate is never under 44.1 kHz, and if the audio device stalls (after a CPU overload in another application, sleep or a sample-rate change), PianoToLife reopens it by itself within about 2 s.</td></tr>
</table>

### Also in 9.5.0

<table>
<tr><td>🎹 <b>Una corda for every piano</b></td><td>A new <b>Una Corda</b> selector next to the pedal mode. <b>BP</b> (default) sends the soft pedal (CC67) to your piano, as before: use it if your piano has its own una corda samples. <b>Simu</b>: PianoToLife makes the una corda itself, for any piano. Each note struck with the soft pedal is played at the velocity that gives <i>this</i> piano the softer, rounder sound of a una corda (measured on real una corda recordings, then adapted to each piano from its model). PianoToLife also adds the soft halo of a real grand: with the soft pedal, the hammer strikes one string less, and that free string rings in sympathy with the others. Your velocity curve still applies: the una corda velocity is computed after it.</td></tr>
<tr><td>🎚 <b>Layer detector</b></td><td>In the Velocity panel, choose a note and click <b>ANALYSE</b> (LAYERS in 9.5.0): PianoToLife plays it at the 127 velocities (about 1 min 20 s) and finds your piano's real velocity layers, whatever their volume. Useful to shape your velocity curve. The result is shown in the tooltip; <b>EXPORT</b> saves it as a text file. Before running, switch off in the piano anything that varies or blends the samples (smear, progressive velocity, key noise, resonance, reverb).</td></tr>
<tr><td>🎙 <b>A richer capture</b></td><td>The capture now also records short strikes at 8 velocities (about 35 minutes in total since 9.5.2, done once), warns you if anything clipped, and cleans the model automatically. These strikes adapt the una corda to your piano. Models captured before still work (they use a general una corda). New built-in Steinway D-274 model.</td></tr>
<tr><td>📁 <b>Remembered folders</b></td><td>Load MIDI, Save MIDI and Bounce open the last folder you used.</td></tr>
</table>

### Also in 9.4.7

<table>
<tr><td>🎹 <b>Velocity by points</b></td><td>The velocity curve is now a line of points you can drag (double-click to add or remove a point). The CURVE knob quickly writes a smooth curve. COPY and PASTE exchange the curve as text, in a common text format, so you can reuse a curve made for your keyboard in other piano software, or share yours. Example:<br><code>Velocity = [0, 49, 66, 77, 85, 95, 102, 108, 114, 121, 127; 0, 9, 12, 19, 31, 51, 68, 88, 116, 127, 127]</code><br>The first list is the velocity you play, the second the velocity sent to the piano. Slope is gone: sessions that used Curve or Slope open with the same touch, as points.</td></tr>
<tr><td>🦶 <b>Cleaner damper lift</b></td><td>When you press the pedal, the freed strings now carry the sound of the dampers lifting, without the diffuse noise on top.</td></tr>
</table>

### Also in 9.4.6

Some fixes and half pedal improvements.

### Also in 9.4.4

<table>
<tr><td>🎵 <b>No more phantom staccato</b></td><td>In Host Sustain, a note struck again at the very moment the pedal comes up could be cut short, even with the key still held. Fixed.</td></tr>
<tr><td>🔔 <b>Ring follows the dampers</b></td><td>With fast dampers, the Ring of the undamped strings could ring on alone after the release and sound too bright. It now follows the damper speed; at the default setting nothing changes.</td></tr>
<tr><td>🪶 <b>Damper Damping stops at -40 %</b></td><td>Faster dampers don't exist on a real grand and could give a bright or rubbing release. Older sessions below -40 % open at -40 %. For a drier staccato, use <b>Release Decay</b>.</td></tr>
<tr><td>🎹 <b>Keyboard: Standard = the reference release</b></td><td>In Standard, every key release sounds like the calibrated normal release, whatever your keyboard sends; the Note-Off curves have no effect there and are greyed out. Before 9.4.2, keyboards sending high release values got a firmer, shorter release and low values a longer one; now all sound the same in Standard. To shorten or lengthen the release, use <b>Release Decay</b>; to play with your keyboard's real release speed, choose <b>Release Velocity 1-127</b> (or your keyboard's own mode) and shape it with the <b>Note-Off Velocity Curve</b>.</td></tr>
<tr><td>⌨️ <b>Release Velocity 1-127 and Key Noise</b></td><td>Very low release values, often sent by mistake on an ordinary release, are read as a slow release, never an endless one. The Key Noise now follows the Note-Off Velocity Curve too (a normal release sounds as before). The Keyboard Note-Off Curve is only active in the N1X and P-525 modes.</td></tr>
</table>

### Also in 9.4.3

<table>
<tr><td>🎹 <b>Kawai VPC1 mode</b></td><td>For Kawai VPC1 owners. The VPC1 measures the key release, but never above about 100, and a slightly slow release easily sends 1 (sometimes 0): taken literally, ordinary releases ring on much too long. The new <b>Keyboard: Kawai VPC1</b> mode reads it so that normal releases sound like a normal damper and slow releases stay natural, never endless. If it does not suit your playing, adjust the <b>Note-Off Velocity Curve</b>, or go back to <b>Keyboard: Standard</b>.</td></tr>
<tr><td>🔌 <b>Standalone: MIDI reconnects by itself</b></td><td>After a short USB drop (heavy CPU load, another audio application), the MIDI keyboard could stay silent until the application was restarted. It now reopens on its own.</td></tr>
</table>

### Also in 9.4.2

> **Capture a model of each piano you use.** The resonance now follows the exact partials of the model: with the model of another piano, many strings no longer match and the resonance gets poorer. Click **Capture** on each of your pianos (see "For a clean capture" below). **Models captured before 9.4.0 should be captured again**: the capture is much richer since 9.4.0. The built-in Steinway D-274 model is ready to use.

<table>
<tr><td>🎶 <b>A selective resonance</b></td><td>Each free string now answers only the partials of the notes that really match it, within about 1.5 Hz (a little more in the high treble), as on a real grand: a clearer sustain "harp", cleaner chords, and the small detunings between strings that make a real piano sound alive.</td></tr>
<tr><td>🎛 <b>Fullness and Shimmer</b></td><td>Two settings replace Coupling. <b>Fullness</b> (default 100 %): how much every free string answers on its lowest partials, the body and the bass fundamentals. <b>Shimmer</b> (default 25 %): how much the free strings answer on their upper partials, the brilliance of the harp; the bass strings get less of it. Inharmonicity is no longer needed and has been removed.</td></tr>
<tr><td>🎚 <b>Resonance Level recalibrated</b></td><td>3 dB lower at the same setting, matched to the real sustain of a concert grand library.</td></tr>
<tr><td>🎹 <b>Keyboard modes</b></td><td><b>Standard</b> (default) works with every keyboard: a key release always sounds like a normal release. Choose <b>Release Velocity 1-127</b> if your keyboard sends real release velocities or behaves in its own way. N1X and P-525 unchanged. A keyboard that still behaves differently? Please tell us.</td></tr>
<tr><td>🐞 <b>No more long release tails</b></td><td>Keyboards that send a release velocity of 0 no longer make some harmonics ring for seconds after short notes.</td></tr>
<tr><td>⚙️ <b>New defaults</b></td><td>Sessions and presets saved with earlier versions open with Harmonic Balance 25 %, Fullness 100 % and Shimmer 25 %.</td></tr>
</table>

### Also in 9.4.0

> **The capture is much richer since 9.4.0**: up to 255 partials per note instead of 48, so the bass strings keep the high harmonics that make the bright "harp" of a real sustain. Models captured before 9.4.0 still work, but capture again to get the new sound.
>
> **For a clean capture**, set up the hosted piano before clicking **Capture**:
> - its output **as loud as possible without clipping** (no red on its meters);
> - **no reverb, no compression, no EQ or other effect** in the piano;
> - **everything switched off in the piano that is not the plain note**: release samples, sustain / pedal resonance, sympathetic / string resonance, key and pedal noises;
> - its **velocity curve set to linear** (no smear or progressive velocity), so the layers found are the piano's real ones (since 9.5.2).
> - Preferably the **close microphones**: room microphones put the hall into the model. If you play with hall microphones, use PianoToLife's **Ambience** (next to Resonance and Release) to put the hall back.

<table>
<tr><td>🎶 <b>A truer sustain "harp"</b></td><td>On a real grand, most of the sustain shimmer comes from the high harmonics of the bass strings. The new capture and model bring them in at their real level: a brighter, calmer sustain. New built-in Steinway D-274 model (1487 partials).</td></tr>
<tr><td>🎛 <b>Harmonic Balance</b></td><td>Harmonic Balance 0-50 %, default 25 % (tuned by ear against the real sustain). Stereo Phase removed. (Coupling, added in 9.4.0, is replaced by Fullness and Shimmer in 9.4.2.)</td></tr>
<tr><td>🎹 <b>A cleaner bass release</b></td><td>Release Weights now 100 % by default (the colour as measured): the weak upper harmonics of the bass no longer stand out after the key release, and the Ring of the undamped strings fades out below E4, as on the reference library. Older sessions open at 100 %.</td></tr>
<tr><td>🦶 <b>Pedal Release Time</b></td><td>Letting the pedal go at once no longer stops the strings abruptly: the dampers land as if the pedal took 80 ms (adjustable 30-200 ms). Slower releases and key releases unchanged. Progressive Dampers is now on for every session.</td></tr>
<tr><td>🎹 <b>A fuller release</b></td><td>The release added after the key release is 6.5 dB stronger, with the register balance measured on a concert grand library: strongest in the low bass (up to 18 dB more from A0 to C1, less and less up to E2). Release Level keeps its Default.</td></tr>
<tr><td>🎸 <b>A truer bass release</b></td><td>Below C3 the release continues up to 48 harmonics (bright wound-string colour up to 1.3-2 kHz) and dies away like a real damper. C3 and above unchanged.</td></tr>
<tr><td>🏛️ <b>Ambience closer to the piano's own room</b></td><td>Measured against the room in a concert grand library's release samples: shorter in the middle range (2.2 s instead of 2.9 s) and much less wide, nearly mono in the low bass. Its Default is now 9 dB higher, matched by ear to VSL's own release room (older sessions open at the new Default).</td></tr>
<tr><td>🔉 <b>Pedal Noise</b></td><td>Optimisations.</td></tr>
<tr><td>🚪 <b>Room choice for Ambience</b></td><td>Next to the Ambience slider: Small, Medium, Default or Hall, same level. The room now surrounds everything PianoToLife adds, noises included; only your piano's own samples stay out.</td></tr>
<tr><td>🎹 <b>The felt plateau</b></td><td>When the damper falls, the string keeps its level for 20-40 ms while the felt settles, then dies away; a slow key release holds it longer. PianoToLife adds this plateau to your piano's notes, on their own harmonics, only adding sound.</td></tr>
<tr><td>🔔 <b>A more natural Ring</b></td><td>After the key release, Ring now mostly makes the undamped top strings sound through their matching harmonics; the beating copies that dominated it below F4 are gone.</td></tr>
<tr><td>📟 <b>Sample rate and buffer at a glance</b></td><td>In the standalone, under the title: the sample rate and buffer the audio really runs at; red with a warning below 44.1 kHz.</td></tr>
<tr><td>🔊 <b>The standalone follows your sound card</b></td><td>At every launch it uses the sample rate your card is running at, not the one saved from the last session; your card, buffer and outputs are still remembered.</td></tr>
</table>

### Also in 9.2.0

Listen to what PianoToLife adds, and more lifelike felts and pedal, rebuilt from measurements case by case.

<table>
<tr><td>🎧 <b>Full Piano = Piano Only + Half/rel/catch Pedal + Symp Res + Release + Noises + Ambience</b></td><td>A listening selector at the top: light one or several parts to hear only them (they add up; none lit = the full piano). Comp, Reverb and Ceiling stay on; no latency. The selection is kept in the preset and the session - e.g. one DAW track per group of parts.</td></tr>
<tr><td>🪶 <b>Felt-Contact (formerly Damper Noise)</b></td><td>The felt touching a string that still vibrates: made from the note's own partials, it now beats gently against the string instead of sounding like a second strike, follows your release speed, and starts as soon as the pedal's dampers first touch the strings (half-pedal too).</td></tr>
<tr><td>🦶 <b>Pedal Noise</b></td><td>A deeper wooden thump, dampers lifting and landing at the right point of the pedal travel, the mechanism's natural delay, a softer slow pedal, and mostly the bass strings ringing after the pedal, as on a real grand.</td></tr>
<tr><td>🏛 <b>Ambience follows Release Level</b></td><td>Release Level off: no end of note in the Ambience. Notes caught by the pedal and strings carried on in half-pedal now go into the Ambience too.</td></tr>
</table>

At the same setting, Pedal Noise and Felt-Contact are louder and fuller than before; everything else opens with the same sound.

### Also in 9.1.8

The idea of 9.1.8: make the **release** clear. On a real piano, the release is part of the resonance: when a
damper lands, the string and its harmonics die away with the rest of the instrument. PianoToLife now shows it
that way, and the choice is simple: your piano's own release, PianoToLife's release (recommended), or a blend
of both.

<table>
<tr><td>🎚 <b>Three levels, side by side</b></td><td><b>Resonance Level</b>, <b>Release Level</b> (formerly Release Noise) and <b>Ambience</b> now sit together at the top, with a bracket showing that the Ambience is the room around both the resonance and the release. The Compact view shows all three.</td></tr>
<tr><td>🔘 <b>Release Level on / off</b></td><td>On by default. Turn it off if you prefer your piano's own release samples; keep it on (recommended) to get the release from the real partials of each string, or lower your piano's release and blend the two.</td></tr>
<tr><td>🎯 <b>"Default" instead of 0</b></td><td>The three levels are in dB around <b>Default</b> (our reference setting, tuned by ear), in the middle of each slider: +3 dB, −6 dB… or Off. In the drawer, every setting reads <b>Default</b> at its default value. Double-click (or Delete) to go back.</td></tr>
</table>

### Also in 9.1.7

<table>
<tr><td>🎹 <b>Every damped string, up to your piano's last damper</b></td><td>Sustain Free To and Max Free Strings now follow <b>Undamped Keys Above</b>: at their maximum they read <b>All</b> and free every damped string, up to the last damper of your piano (Steinway D: G6, Shigeru Kawai: A#6...). Moving Undamped Keys Above sets them to All; you can still lower them.</td></tr>
<tr><td>🎼 <b>Bösendorfer Imperial</b></td><td>Sustain Free To now has two handles. Drag the left one below A0, down to C0, and the pedal also frees the 9 extra bass strings of an Imperial (C0 to G#0), made from the A0 of the resonance model. A subtle, richer bass halo.</td></tr>
<tr><td>🔍 <b>MIDI Monitor, side by side</b></td><td>What PianoToLife receives and what it sends to your piano are on the same line, with one scroll bar. Every difference is in amber: a changed value, a message sent later (with the reason), one added or not sent. The export uses the same two columns. Thanks to Elvis for the idea.</td></tr>
<tr><td>🎵 <b>Crisper staccato in Host Sustain</b></td><td>The short pedal-catch window (about 40 ms) is now only used during a pedal change, where a catch is likely. The rest of the time the Note Off reaches the piano at once, so a staccato played without the pedal is not lengthened.</td></tr>
<tr><td>🎁 <b>Example presets for VSL D-274</b></td><td><code>PianoToLife-Example-Presets-VSL-D274.zip</code> in the release: two Synchron Pianos player presets (STANDARD and FULL) set up to be played through PianoToLife, with a screenshot of the matching PianoToLife settings.</td></tr>
</table>

### Also in 9.1.6

<table>
<tr><td>🎹 <b>Yamaha hybrids: repeated notes</b></td><td>N1, N1X and P-525 repeat a note before the key is fully up, like a real grand. PianoToLife now follows it: the release velocity is measured on the key's last movement (a key that stops halfway no longer counts as a very slow release), and in Host Sustain a note struck again replaces the previous strike if at least as loud, or rings over it if softer.</td></tr>
<tr><td>🤫 <b>Disklavier / N1 silent key</b></td><td>Aftertouch 127 frees the string and aftertouch 0 lets the damper fall back, read directly as the keyboard sends them: no hidden note, no changed velocity. Tested on a real AvantGrand N1.</td></tr>
<tr><td>🔍 <b>MIDI Monitor export</b></td><td>Times in seconds, a resizable window and <b>Export...</b> to a text file, to see exactly what your keyboard sends and what reaches your piano.</td></tr>
<tr><td>✨ <b>And more</b></td><td>One key noise per release, the standalone MIDI player plays files exactly as recorded, Stop never leaves a note stuck.</td></tr>
</table>

### Also in 9.1.4

<table>
<tr><td>🤫 <b>Silent Key list</b></td><td>Off, ≤ 1 (default), ≤ 2, ≤ 3, or <b>Disklavier / N1</b>: silent presses sent as aftertouch 127 (Yamaha AvantGrand N1, Disklavier XP) lift the damper so the string resonates, without playing a note. A real strike on a key held silently takes over smoothly.</td></tr>
<tr><td>🔍 <b>MIDI Monitor</b></td><td>See the MIDI received (<b>Before</b>) and the MIDI sent to your piano (<b>After</b>), side by side; silent keys in grey.</td></tr>
<tr><td>🪟 <b>Comfort</b></td><td><b>ALL DEFAULT</b> button, zoom remembered (90 % the first time), an <b>Auto open</b> check box to choose whether the piano's window opens by itself after loading, and Multicore Processing on by default.</td></tr>
</table>

### Also in 9.1.2

<table>
<tr><td>🎨 <b>A new interface</b></td><td>Envelope, Timbre, Strings and Pedal &amp; Release fold away in one <b>Resonance drawer</b>; closed, it shows the strings and dampers of a grand piano with the resonance rising from them. Level &amp; Pitch and Pedal Noise stay in view.</td></tr>
<tr><td>🎯 <b>0 % = our setting</b></td><td>Every setting in the drawer reads <b>0 % at its default</b>, from −100 % to +100 %. Double-click (or Delete) to go back; the tooltip still shows the real value.</td></tr>
<tr><td>🔁 <b>Natural repeated notes</b></td><td>In Host Sustain, a softer strike under the pedal now rings over the previous one, as on a real piano: a soft repeat no longer cuts a loud note still sounding (most audible in the bass). A strike at least as loud replaces them.</td></tr>
<tr><td>♿ <b>Screen readers</b></td><td>Windows Narrator / NVDA and macOS VoiceOver: every control has a spoken name and help, Tab follows a logical order, and sliders can be moved from the keyboard.</td></tr>
<tr><td>🪶 <b>Damper Noise COLOR</b></td><td>New knob: darker or brighter felts, same level (Damper Noise is now Felt-Contact).</td></tr>
<tr><td>🪟 <b>Hosted piano window</b></td><td>Opens by itself when an instrument or a preset you chose has finished loading, centred on PianoToLife.</td></tr>
<tr><td>✨ <b>And more</b></td><td>Shorter tooltips, message boxes and menus in the interface colours, Ambience at 25 % when switched on, a simpler pedal menu (Host Sustain 2 removed: its sessions open in Host Sustain).</td></tr>
</table>

### Also in 9.0.4

🐞 **Important fix:** no more stray notes when changing chords with the pedal (old notes could come back as pure, slightly out-of-tune tones).

### Also in 9.0.2

<table>
<tr><td>✨ <b>New name</b></td><td>SympResHost is now <b>PianoToLife</b>. Same plug-in: your sessions and presets open as before.</td></tr>
<tr><td>🎹 <b>Upright key noise</b></td><td>GRAND or UPRIGHT action under KEY NOISE.</td></tr>
<tr><td>🦶 <b>Half pedal</b></td><td>A held half pedal decays naturally in one slope; the resonance follows the dampers through the whole zone; slow pedal-ups are seamless.</td></tr>
<tr><td>🎼 <b>Pedal on held notes</b></td><td>Press the pedal after the attack while still holding the keys (syncopated pedalling): the resonance now blooms in about a second, a little less the later the pedal comes, richer on chords. New <b>Held</b> control next to Pedal Catch to make it bolder or subtler.</td></tr>
<tr><td>🎯 <b>Re-pedalling and catch</b></td><td>Quick re-pedals keep their energy like a real piano; the catch is crisper in the treble, fuller in the bass.</td></tr>
<tr><td>🎚 <b>Better defaults</b></td><td>Resonance Level 0 dB is 3 dB richer (old sessions sound the same); Harmonic Balance (formerly Mode Weights) centred on a natural balance of octaves and harmonics; Pedal Damper Curve 32; Inharmonicity 50 ct; Half Pedal Damping 25–95; quieter Key / Pedal Noise at 0 dB (old sessions sound the same).</td></tr>
<tr><td>🖥 <b>Standalone</b></td><td>First launch opens at your audio card's own sample rate with a 256-sample buffer.</td></tr>
<tr><td>🎨 <b>Themes</b></td><td>NOIR &amp; OR, GRAPHITE, NOIR &amp; ROUGE or CLASSIC, chosen in the title bar.</td></tr>
</table>

All the details in the <a href="../../releases/latest">release notes</a>.

### Also in 8.2.12

- **Musical half pedal**, **realistic pedal catch**, **Damper Noise** (felts on the vibrating strings) and a
  **MIDI player / recorder** with 16-bit bounce in the standalone app.

### Also in 8.2.11

- **About 2× faster** resonance engine, same sound.
- **Wooden key action** and **wooden pedal** (Key Noise, Pedal Noise with VOL / MECH).
- **Output Ceiling** (true-peak limiter), TRUE PEAK and LUFS meters.

### Earlier versions

Multicore Processing (8.2.8), re-pedaling with the note's own string, Damper Slope and Release Decay (8.2.6), Ambience, Velocity Curve and the Windows installer (8.2.4), Key Noise and Pedal Noise
(8.2.1), N1X release velocity and Compact view (8.2.0), the pedal modes (8.0.98) and everything before: see the notes of each version in
[Releases](../../releases).

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
unique to that instrument (about 35 minutes, done once). Since 9.5.0 it also records
short strikes at up to 8 velocities (since 9.5.2 in the middle of the piano's real layers, found first on A4), which adapt the una corda to your piano, warns you if anything
clipped and cleans the model automatically. A model of the VSL Synchron
Steinway D-274 (V8) is included and ready to use.

Since 9.4.2 the resonance follows the exact partials of the model, string by string: **capture
a model for each piano you use**. With the model of another piano, many strings no longer
match and the resonance is clearly poorer.

Before capturing, set the hosted piano **as loud as possible without clipping**, with **no reverb,
compression or other effect**, and with **everything switched off that is not the plain note**
(release samples, sustain / pedal resonance, sympathetic resonance, key and pedal noises),
and with the piano's own **velocity curve set to linear** (no smear or progressive velocity).
Preferably the close microphones: room microphones put the hall into the model. If you play with hall microphones,
use PianoToLife's Ambience (next to Resonance and Release) to put the hall back.

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
  **Una Corda: BP**, your piano's own una corda samples play as before.
- **Layer detector and velocity calibration.** Find your piano's real velocity layers on A4
  in about 1 min 20 s, then calibrate its dynamics on a real concert grand, grand or upright;
  export the result as text.
- **Key and pedal noises.** A wooden key action (hammer back on its rest, key landing,
  repetition in the escapement), and a sustain pedal with its wooden thumps, the felts on the
  strings and the freed (mostly bass) strings ringing — following the pedal's travel and speed,
  each with its own volume.
- **Felt-Contact.** The felt touching a string that still vibrates when a key or the pedal lets
  the damper fall, made from each note's real partials and following your release speed, with
  its own volume and colour.
- **Listen to each part.** Full Piano = Piano Only + Half/rel/catch Pedal + Symp Res + Release + Noises + Ambience:
  hear any combination of parts, kept in the preset.
- **MIDI player (standalone).** Load, play, record and save MIDI, and bounce to a 16-bit /
  44.1 kHz WAV — to compare settings on exactly the same performance.
- **Output Ceiling and meters.** A transparent true-peak safety limiter, TRUE PEAK MAX and
  LUFS short-term / long-term.

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

- **PianoToLife's release (recommended)**: turn the release off in your piano (e.g. VSL:
  Release at −inf) and keep **Release Level** on. The release comes from the real partials of
  each string and follows the resonance, the dampers and the **Ambience**.
- **Your piano's own release**: untick **Release Level**, and keep the release of your piano.
- **A blend of both**: keep your piano's release a little lower and adjust **Release Level**
  around **Default**: PianoToLife adds what the samples lack (brighter high harmonics, the
  shimmer of the duplex scale, a longer, beating decay in the bass).

What the re-simulated release contains:

- **Up to 24 partials** of the string, taken from the real sound of your piano, continue
  and die away as the damper settles (**Fast** makes the damper contact more immediate).
- **Ring**: part of the energy passes through the bridge into the **undamped treble
  strings** and the **duplex scale**, which keep shimmering briefly, as on a real grand.
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
  multicore engine like VSL's looks spread out. Compare the whole CPU, and above all listen for
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
Some pianos, such as the **VSL Synchron** pianos, give no way to turn off their sustain
effect or their pedal-down samples. Host Sustain keeps the pedal away from the piano: it
only plays its pedal-up (dry) samples, and PianoToLife holds the notes itself. Half
pedal, pedal catch, sostenuto and restriking are all included. A note struck again under the
pedal behaves like a hammer on a string that still vibrates: a **softer** strike rings over the
previous one (a loud note is never cut by a soft repeat), a strike **at least as loud** replaces
it. **Every strike gets its own Note Off** when the note is finally released,
so pianos that keep one voice per strike (Korg SX2 VST) or count the keys (UVI pianos)
never keep a note hanging. It works with every piano tested: **VSL, Kontakt libraries,
Ivory, Korg SX2 VST and UVI pianos**.
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
hold (e.g. **Native Instruments Session Keys**). A softer restrike starts at the level the previous
strike still had (from its decay in the piano model), so the sound does not drop. Set up the piano
exactly as for Host Sustain.

Changing pedal mode (or una corda mode) lifts the pedals for everyone until you move the pedal again.

**Pedal: Pass-through.**
The piano receives your pedal and handles its own dampers, half-pedal and releases.
In the piano:
- turn off its **sustain samples** (pedal-down samples / "pedal resonance");
- turn off its **sympathetic resonance / string resonance**;
- **keep** its *half-pedal* and *repedalling* options.

Set **Half Pedal Damping Start / Full** to match your piano (defaults match the VSL
Steinway D-274).

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
Please contact me at [olivier.frappier@live.fr](mailto:olivier.frappier@live.fr) before publishing anything: together we will set up its
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
