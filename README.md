# PianoToLife 10.1.6

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

## Also in 10.1.5

**ALIGN ATTACKS now aligns every microphone.** Each sample of each microphone starts 3 ms before its own strike.
Badly cut libraries (strikes up to 15 ms late, microphones cut separately) now play tight and in phase: no more clicks
on the distant microphones, steady timing across the velocity layers. Run ALIGN ATTACKS again on your sets to get it.

Also: RENAME and SAVE use the name of the set's file (no more "My piano").

## Also in 10.1.4

**Important fix — repeated notes in SAMPLER mode**, keys up and under the sustain pedal: a new strike no longer cuts
the previous one; it goes on, a little lower, as on a real piano (up to 4 voices per key, "Per key" in MIX).

Also: **AUTO NAME** reads more naming styles (see *Naming your samples*), **RENAME** of a set in EDIT, and a red
**velocity line** with SELECT BY MIDI.

## Naming your samples (AUTO NAME)

The key is found from the sound; the **layer** is safest from the name. AUTO NAME (on by default) uses it when every
layer of a key carries one of these, as a separate word: dynamics `Piano_C4_mp.wav` (ppp … fff), velocity range
`Piano_C4_033-064.wav`, velocity `Piano_C4_v64.wav`, layer number `Piano_C4_L3.wav`. Use one style for the whole
library; a note, a microphone (`mic2`) or a round robin (`rr2`) is never read as a layer.

## Also in 10.1.2

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

## Also in 10.1.0 — the built-in sampler

PianoToLife can now **play your own piano samples**, without a hosted piano. Switch **HOST / SAMPLER** at the top of the window: in SAMPLER, the hosted piano is set aside and PianoToLife's own sampler plays, with all of PianoToLife's engines on it (sympathetic resonance, release, una corda, pedals).

> **Who is PianoToLife for?** It is made for **sampled pianos** — the libraries you already own, or your own piano, which you can sample with up to 5 microphones. Its auto-mapping places the velocities, the attacks, the tonal colours and the dynamics as on a real piano: a fast and powerful sample editor, built on a sampling / modelling approach. Purely modelled pianos already compute their own resonance and pedal behaviour, so PianoToLife has little to add to them: it is not intended for hosting them.

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
- **BODY** (MIX): the perceived size of the piano — every note's own fundamental raised or lowered, fully in the bass and the middle, fading out in the treble.
- **TRUE PEAK** (MIX): per microphone and for all 5 together, 4 x oversampled; red as soon as it clipped, until you reset it.
- **Protected sets**: every save hides the samples in an encrypted container (`.wptl`), rewritten only when samples change. A password protects **EDIT**, never playing. A set saved on Mac opens on Windows and back.
- **Presets**: SAMPLER presets are marked `[SAMP]` and kept in `Presets/Sampler`; the preset list follows the mode.
- **Tuning**: SR Transpose, SR Fine Pitch and SR A4 Tuning play on the sampler; the A4 measured by RECAL is sent to SR A4 Tuning, so 440 Hz plays the set as recorded.

HOST mode is unchanged: everything from 9.5.3 is there.

## Distributing sampled pianos made with PianoToLife

Making sample sets with PianoToLife and playing them for your own use is free.
**Any public distribution of a sampled piano made for PianoToLife's sampler** (sample sets,
`.ptlset` / `.wptl` files, `[SAMP]` presets), **free or paid, requires my prior authorization.**
Please contact me at [olivier.frappier@live.fr](mailto:olivier.frappier@live.fr) before publishing anything: together we will set up its
protection (encrypted container, password) and the way it is distributed.


## Example presets for VSL Synchron Pianos D-274
**PianoToLife-Example-Presets-VSL-D274.zip** (in the assets below): two presets for the Synchron Pianos player, made to be played through PianoToLife (STANDARD and FULL, `.vsynpreset`), and a screenshot of the PianoToLife settings used with them. They work on Mac and Windows, in AU and VST3: load them from the preset menu of Synchron Pianos.

## Download
See the assets below (Mac: AU, VST3, standalone; Windows: installer, VST3, standalone).
