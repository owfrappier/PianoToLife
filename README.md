<h1 align="center">SympResHost</h1>
<p align="center"><b>Bring your VST / AU piano to life — and to realism.</b></p>
<p align="center">Replace your piano's static sympathetic resonance samples and canned pedal behaviour<br>
with one live, physically modelled string engine — from a single held key to every damper lifted.</p>

<p align="center">
  <img src="docs/screenshot.png?v=3" alt="SympResHost interface" width="900">
</p>


<p align="center">
  <a href="../../releases/latest"><b>⬇ Download the latest release</b></a> ·
  macOS 14+ (Apple Silicon) · Windows 10/11 x64 (experimental) · AU · VST3 · Standalone
</p>

---

## What's new in 8.2.0

- **Release velocity for Yamaha N1X — now sent to your piano.** SympResHost measures how
  fast each key comes back (the N1X reports the key position only while it returns) and
  turns it into a real note-off velocity. SympResHost's dampers, its simulated release
  **and the hosted piano** (Pianoteq, VSL, Kontakt…) all receive it. The Yamaha P-525 mode
  already worked this way.
- **Keyboard Note-Off Curve** (N1X and P-525): shapes the note-off velocity sent to the
  hosted piano — useful with pianos that have no release-velocity curve of their own.
- **Compact view:** fold SympResHost into a small bar (pedal mode and resonance level) and
  expand it again with one click. Sound and settings are not affected.
- **Max Free Strings (CPU):** the main CPU control, now named as such — lower it on a
  slower computer.
- The pedal **DEFAULT** button also brings the pedal mode back to **Host Sustain**.

### Also in 8.0.98

- **Clearer pedal modes:** **Host Sustain** (default) works with every piano tested — VSL,
  Kontakt libraries, Ivory, Korg SX2 VST, UVI pianos; **Host Sustain 2** is a fallback;
  **Pass-through** for pianos that handle the pedal themselves. See
  [Pedal mode](#pedal-mode-host-sustain-host-sustain-2-or-pass-through).
- **Sustain Samples Off retired** (it could raise the CPU load a lot in VST3 with the
  pedal down). Older sessions open in Host Sustain.
- **Restriking under the pedal:** no damper noise in the middle of the pedal, and no more
  hanging or phantom notes (Kontakt, Korg SX2, UVI).
- **Cleaner interface:** setup hint for the selected pedal mode, grouped resonance
  controls, Keyboard menu, uniform DEFAULT buttons.

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

Each piano can be **calibrated precisely** with the built-in **automatic capture**.
SympResHost plays the **88 notes pedal up**, one by one, and analyses the real partials,
their tuning, their inharmonicity and their decay times. It then builds a resonance model
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
  progressively instead of being cut. This includes the high harmonics, the duplex scale,
  the undamped treble strings and the slow beating of the bass unisons. It can replace
  weak or missing release samples, or blend with the ones your piano already has.
- **Honest colour.** Measured inharmonicity, per-string decay times, the colour of strings
  driven through the bridge (not by the hammer), and an optional microphone-pair stereo
  image.
- **Damper mechanics view.** A live, realistic view of the dampers and strings, at no
  CPU cost.
- **Compact view.** Fold the interface into a small bar while you play.

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
natural. There is no switching or cross-fading between two effects, only the same strings
being freed or damped.

### The release, too

When a key is released or the pedal comes up, the dampers do not cut the sound like a
switch. The felt lands on the vibrating string and damps it progressively, some partials
dying faster than others depending on where the damper touches the string.
SympResHost **re-creates this release**. The string's own partials, taken from the real
sound of your piano, die away gently as the damper settles, with a lighter or firmer touch
depending on how you release the key or the pedal. With half-pedalling, the dampers resting
lightly on the strings keep damping them softly instead of stopping them.

### Replace, complete or blend your piano's release samples

Release samples vary a lot from one virtual piano to another: some are rich, some are
weak, some are missing altogether. The release re-simulated by SympResHost adapts to all
three cases:

- **Missing or very weak release samples** (e.g. Ivory 3, or a release you turned off):
  raise **Release Noise**, and SympResHost provides the whole release on its own.
- **Average release samples**: keep a low setting (the default is 3 %). The simulation
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
- The **Keyboard** menu adapts SympResHost to keyboards that report the release in their
  own way:
  - **N1X or others** (Yamaha N1X and similar Yamaha hybrids): these instruments report
    the key position through polyphonic aftertouch, only while the key comes back.
    SympResHost measures the time the key takes to return and turns it into release
    velocity (no aftertouch at all = a very fast release). It can filter the aftertouch
    and CC19 messages so the hosted piano does not receive them.
  - **Yamaha P-525**: measures the timing of the release information the P-525 sends and
    turns it into release velocity.
  - In both modes the result **replaces the note-off velocity sent to the hosted piano**,
    shaped by the **Keyboard Note-Off Curve**. The **Note-Off Velocity Curve** only shapes
    how SympResHost's own dampers and release respond.
- The speed at which you **lift your foot off the pedal** shapes the damping of all the
  strings in the same way.
  - **Progressive dampers** (on by default): a light damper contact — a slow key or pedal
    release, or half-pedalling — silences the upper partials first while the fundamental
    lingers, like a real grand. A firm contact stops every partial together. Turn
    **Progressive** off to get the previous damping.
- **Pedal Damper Curve** does for the pedal what the note-off curve does for the keys: it
  sets how the speed and position of your foot become damper contact (default 16; lower =
  gentler, more lingering; higher = firm contact sooner).

## Requirements

| | macOS | Windows (experimental) |
|---|---|---|
| **System** | macOS 14 Sonoma or later | Windows 10 / 11, 64-bit (x64) |
| **Processor** | Apple Silicon (M2 or later recommended). Intel Macs are not supported. | Intel / AMD x64 (also runs on Windows on ARM through emulation) |
| **Formats** | Audio Unit, VST3, Standalone application | VST3, Standalone application (ASIO) |
| **Hosted piano** | Any AU or VST3 piano plug-in built for Apple Silicon | Any x64 VST3 piano plug-in, installed in `C:\Program Files\Common Files\VST3` |

On macOS, the plug-in does not load in a host running under Rosetta.

### macOS

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

### AU or VST3? (macOS)

Use SympResHost in the **same format as your DAW**, and host a piano **in that same format**:

| You use | SympResHost to insert | Pianos offered |
|---|---|---|
| Logic Pro, GarageBand, MainStage | **AU** | AU pianos |
| Cubase, Reaper, Studio One, Live… | **VST3** | VST3 pianos |
| Standalone app | — | AU and VST3 pianos |

- An older session or preset whose piano is in the other format reopens with its
  SympResHost settings, but **without the piano**: just choose the piano again in the
  right format.
- Instruments that exist only as VST3 cannot be hosted in SympResHost AU (and vice versa).
- In the standalone app, avoid switching from the VST3 to the AU of the same instrument:
  SympResHost will offer to restart.

### Windows (experimental)

1. Download `SympResHost-<version>-Windows-x64-Experimental.zip` from
   [Releases](../../releases/latest) and unzip it.
2. **VST3 location:** SympResHost only scans `C:\Program Files\Common Files\VST3`. Make sure
   your piano's VST3 is there (move it or re-run its installer if needed).
3. To use SympResHost in a DAW, copy the **whole** `SympResHost.vst3` folder to
   `C:\Program Files\Common Files\VST3`.
4. The `.exe` is not digitally signed yet: if Windows shows *"Windows protected your PC"*,
   click **More info → Run anyway**.
5. Standalone: **Options → Audio/MIDI Settings…**, choose **ASIO** and your audio
   interface's driver (or ASIO4ALL / FlexASIO), then **Scan VST3** and load your piano.

Tested in Ableton Live 12 (VST3).


## Setting up your piano (important)

SympResHost provides the resonance and the sustain behaviour itself, and it listens to
the **dry** sound of your piano to drive the strings. So, **in the hosted piano**:

- **turn off** every *sympathetic resonance*, *string resonance*, *sustain resonance* or
  *pedal resonance* option;
- **turn off all reverb, effects and compression** (convolution rooms, ambience, EQ /
  "tone" effects, limiters, stereo wideners…). Otherwise the resonating strings would be
  fed with the room and the effects instead of the strings, and the calibration capture
  would measure them too;
- then follow the setup of your **pedal mode** below (sustain samples, key noise).

Need a room or some compression? Use **SympResHost's own Piano Comp and Reverb**
instead: they are placed *after* the resonance engine, so the resonance stays clean and
the whole instrument goes through the same room. Any other effect can of course be
inserted after SympResHost in your DAW.

Remember that the CPU load shown by your DAW for SympResHost **includes the hosted piano**,
with its own settings and number of microphones.
On a slower computer, or if the CPU load is too high with the pedal down, lower
**Max Free Strings (CPU)**: fewer strings resonate at the same time, for a slightly
thinner halo.

### Pedal mode: Host Sustain, Host Sustain 2 or Pass-through?

**What are "sustain samples"?** Many sampled pianos contain two sets of recordings of
every note: one played with the pedal **up**, and one with the pedal **down**. The
pedal-down recordings include the sympathetic resonance of the whole instrument,
*frozen at the moment of the recording*. SympResHost builds this resonance itself, live,
from the strings that are really free at each instant. If the piano also plays its
pedal-down samples, the resonance is there twice, and the frozen one does not follow
your pedalling.

The pedal section of SympResHost shows what to turn off in the piano for the selected
mode.

**Pedal: Host Sustain (default) — designed for pianos that do not let you turn off their sustain.**
Some pianos, such as the **VSL Synchron** pianos, give no way to turn off their sustain
effect or their pedal-down samples. Host Sustain keeps the pedal away from the piano: it
only plays its pedal-up (dry) samples, and SympResHost holds the notes itself. Half
pedal, pedal catch, sostenuto and restriking are all included. When you restrike a note
under the pedal, **every strike gets its own Note Off** when the note is finally released,
so pianos that keep one voice per strike (Korg SX2 VST) or count the keys (UVI pianos)
never keep a note hanging. It works with every piano tested: **VSL, Kontakt libraries,
Ivory, Korg SX2 VST and UVI pianos**.
In the piano, turn off:
- **all Key Noise / release noise** (SympResHost sends the Note Offs when the pedal comes
  up, so these noises would come at the wrong moment);
- its **sympathetic resonance / string resonance**, including pedal-up resonance.

With Host Sustain, half-pedalling keeps the piano's clean pedal-up sound while
SympResHost's resonance fades progressively (treble dampers first). The result is a real
gradient, even with pianos whose own half pedal only switches between full samples.

**Pedal: Host Sustain 2 — fallback.**
Same as Host Sustain, but a note restruck under the pedal gets a **single Note Off** when
it is released (the previous behaviour). Set up the piano exactly as for Host Sustain.

> Start with **Host Sustain**. Choose **Host Sustain 2** only if a piano plays extra
> release noises or misbehaves when restruck notes are released.

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
| **VSL Synchron Steinway D-274** | Host Sustain | Reference: default settings are tuned on it. VSL does not let you turn off its sustain samples. Turn off Key Noise, reverb and compression in VSL; use the **close mics** as much as possible. Confirmed on Mac and Windows (Intel Ultra 9 285H, 64-sample buffer). |
| **VSL Synchron CFX** | Host Sustain | Works well ("they sound really good"). Key Noise off in VSL. |
| **VSL Synchron Concert D 1887** | Host Sustain | Works well with a captured SR model. |
| **VSL Synchron Imperial** | Host Sustain | Not tested yet — feedback welcome. Some low-register partials may be missing. |
| **Kontakt pianos** (e.g. The Grandeur) | Host Sustain | Work well. Turn off Key Noise and the sympathetic / string resonance of the instrument. Pass-through also works if the instrument lets you turn off its sustain samples. |
| **Ivory 3** (Synthogy) | Host Sustain or Pass-through | Works in both modes. Turn off *Sympathetic Resonance* in the Ivory preset (and *Sustain* in Pass-through). To our ears the resonance and sustain even sound better than Ivory's built-in ones — a subjective opinion, not a promise. |
| **Pianoteq** | Pass-through | Turn off Pianoteq's sympathetic resonance. |
| **Korg SX2 VST** | Host Sustain | Keeps one voice per strike; Host Sustain gives each strike its own Note Off, so restruck notes stop correctly. |
| **UVI Modern D** | Host Sustain | Works, and a restruck key no longer stays drawn down. |

Other VSL pianos: use **Host Sustain**, with Key Noise turned off in VSL.


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
[issue](../../issues) with the piano name, its version, your pedal mode and your
SympResHost settings.

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
Instruments, Korg, Pianoteq / Modartt, Yamaha CFX and Bösendorfer Imperial are trademarks
of their respective owners.
SympResHost is an independent product and is not affiliated with, endorsed by or
sponsored by any of them. "Steinway D-274" designates the sampled instrument used for the
built-in resonance model.<br>
VST is a registered trademark of Steinberg Media Technologies GmbH.
Audio Unit and macOS are trademarks of Apple Inc.
</sub>
