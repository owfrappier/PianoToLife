<h1 align="center">SympResHost</h1>
<p align="center"><b>Bring your VST / AU piano to life — and to realism.</b></p>

<p align="center">
  <img src="docs/screenshot.png" alt="SympResHost interface" width="900">
</p>

<p align="center">
  <a href="../../releases/latest"><b>⬇ Download the latest release</b></a> ·
  macOS 14+ · Apple Silicon · AU · VST3 · Standalone
</p>

---

## What it does

Most virtual pianos sound beautiful note by note, yet something is missing as soon as you
really *play*: the halo of strings ringing in sympathy, the bloom of the sustain pedal, the
way a chord changes colour as the dampers lift, the subtle breath of half-pedalling.
Built-in "sympathetic resonance" and "sustain resonance" options are often static,
generic, or simply absent.

**SympResHost** hosts your favourite piano plug-in and adds a physically modelled
**sympathetic resonance and sustain engine** around it.

### Driven by the real sound of your piano

SympResHost does not add a generic reverb or a canned resonance sample. The free strings
are set into vibration by **the actual audio of the piano you play**: every note, every
velocity, every nuance of the samples feeds the resonating strings in real time, exactly
as the soundboard of a real piano carries the vibration of one string to the others.

### Calibrated for each piano

Each piano can be **calibrated precisely** with the built-in **automatic capture**:
SympResHost plays the **88 notes pedal up**, one by one, analyses the real partials,
their tuning, their inharmonicity and their decay times, and builds a resonance model
unique to that instrument (about 35 minutes, done once). A model of the VSL Synchron
Steinway D-274 is included and ready to use.

### Features

- **Every string can resonate.** The resonance comes from a model of the real partials of
  each string, measured from the piano you host. A held key frees its string; the pedal
  frees them all — exactly like the dampers of a real grand.
- **Real half-pedalling.** Resonance and damping follow the pedal continuously, from the
  first touch of the dampers to full sustain. Pedal-up / pedal-down transitions, chords
  caught in the pedal, syncopated pedalling and sostenuto behave naturally.
- **Pedal catch.** Press the pedal just *after* the notes and the strings still sounding
  feed the freed strings — gently, as on a real instrument.
- **Natural string release.** When a damper falls, the partials of the string die away
  progressively instead of being cut — with the high harmonics, the duplex scale, the
  undamped treble strings and the slow beating of the bass unisons. It can replace weak or
  missing release samples, or blend with the ones your piano already has.
- **Honest colour.** Measured inharmonicity, per-string decay times, the colour of strings
  driven through the bridge (not by the hammer), and an optional microphone-pair stereo
  image.
- **Damper mechanics view.** A live, realistic view of the dampers and strings, at no
  CPU cost.

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
SympResHost models exactly that, with a single engine. That is why pedal-up / pedal-down
transitions, half-pedalling, chords caught in the pedal and a single held note all sound
natural: there is no switching or cross-fading between two effects, only the same strings
being freed or damped.

### The release, too

When a key is released or the pedal comes up, the dampers do not cut the sound like a
switch. The felt lands on the vibrating string and damps it progressively, some partials
dying faster than others depending on where the damper touches the string.
SympResHost **re-creates this release**: the string's own partials, taken from the real
sound of your piano, die away gently as the damper settles, with a lighter or firmer touch
depending on how you release the key or the pedal. With half-pedalling, the dampers resting
lightly on the strings keep damping them softly instead of stopping them.

### Replace, complete or blend your piano's release samples

Release samples vary a lot from one virtual piano to another: some are rich, some are
weak, some are missing altogether. The release re-simulated by SympResHost adapts to all
three cases:

- **Missing or very weak release samples** (e.g. Ivory 3, or a release you turned off):
  raise **Release Noise** — SympResHost then provides the whole release on its own.
- **Average release samples**: keep a low setting (the default is 3 %) — the simulation
  blends with the samples and adds what they lack: brighter high harmonics, the shimmer of
  the duplex scale, and a longer, beating decay in the bass.
- **Rich release samples**: turn it down further or off, and let the samples speak.

What the re-simulated release contains:

- **Up to 24 partials** of the string, taken from the real sound of your piano, continue
  and die away as the damper settles (**Fast** makes the damper contact more immediate).
- **Ring**: part of the energy passes through the bridge into the **undamped treble
  strings** and the **duplex scale**, which keep shimmering briefly, as on a real grand.
- **In the bass**, the release lasts longer and the strings of a unison **beat** slightly,
  because they are never damped at exactly the same instant.
- **Release Weights** balances the colour of the release: 100 % keeps the partials as
  recorded; lower values bring up the high harmonics without changing the overall level
  (default 50 %). It works like **Mode Weights** does for the resonance.

### Your release gesture counts

How fast you let a key come up changes how the damper lands, so SympResHost listens to it:

- **Note-off (release) velocity** from any keyboard that sends it: a slow release gives a
  softer, longer damping; a quick one stops the string more firmly. An adjustable curve
  lets you match your keyboard.
- **Yamaha N1X and similar Yamaha hybrids**: these instruments report the key release
  through polyphonic aftertouch. **N1X mode** turns it into release velocity, and can
  filter the aftertouch and CC19 messages so the hosted piano does not receive them.
- **Yamaha P-525**: **P525 mode** measures the timing of the release information the
  P-525 sends and turns it into release velocity, with its own curve.
- The speed at which you **lift your foot off the pedal** shapes the damping of all the
  strings in the same way.

## Requirements

| | |
|---|---|
| **Mac** | Apple Silicon (M2 or later recommended). Intel Macs are not supported. macOS 14 Sonoma or later. |
| **Windows (experimental)** | Windows 10 / 11, 64-bit (x64). VST3 pianos must be in `C:\Program Files\Common Files\VST3`. |
| **Formats** | Mac: Audio Unit, VST3, Standalone — Windows: VST3, Standalone (ASIO) |
| **Hosted piano** | Any AU or VST3 piano plug-in (Mac: built for Apple Silicon — Windows: x64) |

## Installation

1. Download `SympResHost-<version>-macOS-AppleSilicon.pkg` from
   [Releases](../../releases/latest).
2. Double-click it. The installer is signed and notarized by Apple: no security warning.
3. Choose what to install: Audio Unit, VST3 and/or the standalone application.
4. In your DAW, insert **SympResHost** as an instrument, then load your piano inside it
   with **Scan AU + VST3** / **Open AU or VST3**.

Optional integrity check:
```
shasum -a 256 SympResHost-<version>-macOS-AppleSilicon.pkg
```
and compare with the `.sha256` file of the release.

## Setting up your piano (important)

SympResHost provides the resonance and the sustain behaviour itself, and it listens to
the **dry** sound of your piano to drive the strings. So, **in the hosted piano**:

- **turn off** every *sympathetic resonance*, *sustain resonance*, *pedal resonance* or
  *sustain samples* option;
- **turn off all reverb, effects and compression** (convolution rooms, ambience, EQ /
  "tone" effects, limiters, stereo wideners…). Otherwise the resonating strings would be
  fed with the room and the effects instead of the strings, and the calibration capture
  would measure them too;
- **keep** the *half-pedal* and *pedal catch* related options if your piano has them.

Need a room or some compression? Use **SympResHost's own Piano Comp and Reverb**
instead: they are placed *after* the resonance engine, so the resonance stays clean and
the whole instrument goes through the same room. Any other effect can of course be
inserted after SympResHost in your DAW.

### Force Sustain Samples Off — mainly for VSL pianos

**What are "sustain samples"?** Many sampled pianos contain two sets of recordings of
every note: one played with the pedal **up**, and one played with the pedal **down**.
The pedal-down recordings include the sympathetic resonance of the whole instrument,
*frozen at the moment of the recording*: all the strings ringing freely, whatever you
are actually playing.

**Why is that a problem with SympResHost?** SympResHost builds this resonance itself,
live, from the strings that are really free at each instant: pedal, half-pedal,
repedalling, held keys, sostenuto. If the piano also plays its pedal-down samples, the
resonance is there twice, and the frozen one does not follow your pedalling.

**The normal solution:** turn off the sustain samples (or "pedal resonance") in your
piano's own interface. Most pianos offer this option — then you do not need anything
else, and **Force Sustain Samples Off must be unchecked**.

**The VSL case:** the VSL Synchron pianos, in their current versions, do not let you
turn off their pedal-down samples. **Force Sustain Samples Off** solves this without
taking the pedal away from the piano:

1. When you play a note with the pedal down, SympResHost sends the piano a pedal-up
   value for an instant, exactly at the note.
2. The piano starts the note with its **pedal-up** sample (dry, no frozen resonance).
3. The real pedal value is sent back immediately after, so the piano keeps controlling
   its dampers, half-pedalling, repedalling and releases as usual.

The resonance you hear is then only SympResHost's, following your playing.

**Settings:**
- The pedal-up value sent at the note depends on **Half Pedal Damping Start**: set the
  Half Pedal values to match your piano (defaults match the VSL Steinway D-274).
- Works with **AU and VST3**. In VST3 the pedal reaches the piano as a parameter, so
  SympResHost splits the piano's processing at the note to make sure it is seen; this is
  automatic. **AU Split** applies the same method to AU pianos (off by default, not
  needed for the VSL D-274). **Split Length** sets how long the pedal-up value lasts
  (default 16 samples, 0.4 ms).
- Tested with the **VSL Synchron Steinway D-274**.

> **Important — all other pianos: uncheck Force Sustain Samples Off.**
> The option is checked by default because it is needed for the VSL pianos. With any
> other piano (Ivory, Kontakt libraries, Garritan, Pianoteq…), **uncheck it** and turn
> off the sustain samples / pedal resonance in the piano itself. Left on with a piano
> that does not need it, it can make some notes start damped or sound uneven from one
> register to another.
>
> **Tested pianos**

| Piano | Status | Notes |
|---|---|---|
| **VSL Synchron Steinway D-274** | Reference | Default settings are tuned on it. Enable **Force Sustain Samples Off** in SympResHost so VSL does not play its own sustain samples. Use the **close mics** as much as possible and disable **all reverb and compression** in VSL. Confirmed on Mac and on Windows (Intel Ultra 9 285H, 64-sample buffer, no crackling). |
| **Ivory 3** (Synthogy) | Works very well | In the Ivory preset, turn off *Sustain* and *Sympathetic Resonance*; **uncheck Force Sustain Samples Off** in SympResHost. To our ears the resonance and sustain even sound better than Ivory's built-in ones — a subjective opinion, not a promise. |
| **Kontakt pianos** | Should work | Turn off the sustain / sympathetic resonance options of the instrument; **uncheck Force Sustain Samples Off**. |
| **VSL Synchron Concert D 1887** | Being tested | SR capture in progress — should work. Feedback welcome. |
| **VSL Synchron CFX** | Incompatible by default | work with HOST sustain mode only
| **VSL Synchron Imperial** | Not tested yet | Feedback welcome. |

Other VSL pianos: try **Force Sustain Samples Off** if the pedal still triggers the library's sustain samples.


## Enjoying SympResHost?

SympResHost is free, and it took months of listening, measuring and comparing with real
pianos. If it has given your piano a new life, you can say thank you — the price of a
couple of coffees, **10 € or 20 €**, keeps the project moving:

<p align="center">
  <a href="https://www.paypal.com/paypalme/owfrappier"><b>♥ Support SympResHost on PayPal</b></a>
</p>

Every contribution, however small, is read, appreciated and turned into new versions.

## Feedback

Found a piano that works (or doesn't)? Please open an
[issue](../../issues) with the piano name, its version and your SympResHost settings.

## About

SympResHost is developed by **Olivier Frappier**, pianist.
The code was designed and written with the help of **Claude** (Anthropic) and other AI
assistants, guided by many hours of listening tests and comparisons with real pianos.
Built with the JUCE framework.

The source code is not public; this repository hosts the official releases only.

---

<sub>
© 2026 Olivier Frappier. All rights reserved.<br>
Steinway, Vienna Symphonic Library / VSL, Synchron, Ivory / Synthogy, Kontakt / Native
Instruments, Yamaha CFX and Bösendorfer Imperial are trademarks of their respective owners.
SympResHost is an independent product and is not affiliated with, endorsed by or
sponsored by any of them. "Steinway D-274" designates the sampled instrument used for the
built-in resonance model.<br>
VST is a registered trademark of Steinberg Media Technologies GmbH.
Audio Unit and macOS are trademarks of Apple Inc.
</sub>
