<h1 align="center">PianoToLife</h1>
<p align="center"><i>formerly SympResHost</i></p>
<p align="center"><b>Bring your VST / AU piano to life — and to realism.</b></p>
<p align="center">Replace your piano's static sympathetic resonance samples and canned pedal behaviour<br>
with one live, physically modelled string engine — from a single held key to every damper lifted.</p>

<p align="center">
  <img src="screenshot.png?v=914" alt="PianoToLife interface" width="900">
</p>


<p align="center">
  <a href="../../releases/latest"><b>⬇ Download the latest release</b></a> ·
  macOS 14+ (Apple Silicon) · Windows 10/11 x64 · AU · VST3 · Standalone
</p>
<p align="center">
  PianoToLife is free. <a href="https://www.paypal.com/paypalme/owfrappier"><b>♥ Donate with PayPal</b></a> to support its development.
</p>

---

## What's new in 9.1.4

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
<tr><td>🪶 <b>Damper Noise COLOR</b></td><td>New knob: darker or brighter felts, same level.</td></tr>
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

Multicore Processing (8.2.8), re-pedaling with the note's own string, Damper Slope and Release Decay (8.2.6), Ambience, Velocity Curve / Slope and the Windows installer (8.2.4), Key Noise and Pedal Noise
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
unique to that instrument (about 35 minutes, done once). A model of the VSL Synchron
Steinway D-274 is included and ready to use.

### Features

- **Every string can resonate.** The resonance comes from a model of the real partials of
  each string, measured from the piano you host. A held key frees its string; the pedal
  frees them all — exactly like the dampers of a real grand.
- **Real half-pedalling.** Resonance and damping follow the pedal continuously, from the
  first touch of the dampers to full sustain. In Host Sustain, held notes carry on as their
  own string with a fast-dying part and a long residue, like a real grand. Pedal-up / pedal-down transitions, chords
  caught in the pedal, syncopated pedalling and sostenuto behave naturally.
- **Pedal catch.** Press the pedal just *after* the notes and the strings still sounding
  feed the freed strings — gently, as on a real instrument. In Host Sustain, a note caught
  just after its release comes back through its own string, at a level that depends on how
  quickly you catch it; quick re-pedals fade naturally from one to the next. Keys still held when the
  pedal goes down (syncopated pedalling) bloom in about a second, with their own **Held** control.
- **Bass and treble dampers.** Damper Damping and Slope set how fast the dampers stop the
  strings, longer in the bass, shorter in the treble.
- **Natural string release.** When a damper falls, the partials of the string die away
  progressively instead of being cut. This includes the high harmonics, the duplex scale,
  the undamped treble strings and the slow beating of the bass unisons. It can replace
  weak or missing release samples, or blend with the ones your piano already has.
- **Honest colour.** Measured inharmonicity, per-string decay times, the colour of strings
  driven through the bridge (not by the hammer), and an optional microphone-pair stereo
  image.
- **Clear, accessible interface.** The detailed resonance settings fold away in a drawer and
  read 0 % at their default; the whole interface works with screen readers (Narrator / NVDA,
  VoiceOver) and from the keyboard.
- **Damper mechanics view.** A live, realistic view of the dampers and strings, at no
  CPU cost; the strings of the keys still held are shown in orange.
- **Efficient.** A highly optimised engine (about 2× faster since 8.2.11), plus an optional
  multicore mode that shares the resonance between CPU cores.
- **Compact view.** Fold the interface into a small bar while you play.
- **Key and pedal noises.** A wooden key action (hammer back on its rest, key landing,
  repetition in the escapement), and a sustain pedal with its wooden knocks, the felts on the
  strings and the freed strings ringing — each with its own volume.
- **Damper Noise.** The buzz of the felts landing on the vibrating strings, made from each
  note's real partials, with its own volume and colour.
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

### Replace, complete or blend your piano's release samples

Release samples vary a lot from one virtual piano to another: some are rich, some are
weak, some are missing altogether. The release re-simulated by PianoToLife adapts to all
three cases:

- **Missing or very weak release samples** (e.g. Ivory 3, or a release you turned off):
  raise **Release Noise**, and PianoToLife provides the whole release on its own.
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
  (default 50 %). It works like **Harmonic Balance** does for the resonance.
- **Decay** (next to Release Noise) sets the length of the release tail; it also follows
  Damper Damping and Slope, so it is longer in the bass.
- The release belongs to the resonance engine: switching **SYMPATHETIC RESONANCE** off
  switches it off too.

### Your release gesture counts

How fast you let a key come up changes how the damper lands, so PianoToLife listens to it:

- **Note-off (release) velocity** from any keyboard that sends it: a slow release gives a
  softer, longer damping; a quick one stops the string more firmly. An adjustable curve
  lets you match your keyboard.
- The **Keyboard** menu adapts PianoToLife to keyboards that report the release in their
  own way:
  - **N1X or others** (Yamaha N1X and similar Yamaha hybrids): these instruments report
    the key position through polyphonic aftertouch, only while the key comes back.
    PianoToLife measures the time the key takes to return and turns it into release
    velocity (no aftertouch at all = a very fast release). It can filter the aftertouch
    and CC19 messages so the hosted piano does not receive them.
  - **Yamaha P-525**: measures the timing of the release information the P-525 sends and
    turns it into release velocity.
  - In both modes the result **replaces the note-off velocity sent to the hosted piano**,
    shaped by the **Keyboard Note-Off Curve**. The **Note-Off Velocity Curve** only shapes
    how PianoToLife's own dampers and release respond.
- **Silent Key** (list next to SYMPATHETIC RESONANCE): a silent key press lifts the damper
  without playing a note, so the string is free to resonate (play a chord over it, or hold it
  while lifting the pedal). **≤ 1** (default), **≤ 2**, **≤ 3** = notes at that velocity or lower;
  **Disklavier / N1** = polyphonic aftertouch 127 / 0, as sent by the Yamaha AvantGrand N1 and
  Disklavier XP (all velocities play in that mode); **Off** = none. The **MIDI Monitor** button
  shows what arrives and what is sent to the piano.
- The speed at which you **lift your foot off the pedal** shapes the damping of all the
  strings in the same way.
  - **Progressive dampers** (on by default): a light damper contact — a slow key or pedal
    release, or half-pedalling — silences the upper partials first while the fundamental
    lingers, like a real grand. A firm contact stops every partial together. Turn
    **Progressive** off to get the previous damping.
- **Pedal Damper Curve** does for the pedal what the note-off curve does for the keys: it
  sets how the speed and position of your foot become damper contact (default 32 = linear; lower =
  gentler, more lingering; higher = firm contact sooner).

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
- then follow the setup of your **pedal mode** below (sustain samples, key noise).

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

### Pedal mode: Host Sustain, Host Sustain (stacked) or Pass-through?

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
| **VSL Synchron Steinway D-274** | Host Sustain | Reference: default settings are tuned on it. VSL does not let you turn off its sustain samples. Turn off Key Noise, reverb and compression in VSL; use the **close mics** as much as possible. Set **Ambience to about 20 %**: the D-274 samples already contain the hall, even on the close mics (condenser, tube or ribbon). Confirmed on Mac and Windows (Intel Ultra 9 285H, 64-sample buffer). |
| **VSL Synchron CFX** | Host Sustain | Works well ("they sound really good"). Key Noise off in VSL. |
| **VSL Synchron Concert D 1887** | Host Sustain | Works well with a captured SR model. |
| **VSL Synchron Imperial** | Host Sustain | Not tested yet — feedback welcome. Some low-register partials may be missing. |
| **Kontakt pianos** (e.g. The Grandeur) | Host Sustain | Work well. Turn off Key Noise and the sympathetic / string resonance of the instrument. Pass-through also works if the instrument lets you turn off its sustain samples. |
| **Ivory 3** (Synthogy) | Host Sustain or Pass-through | Works in both modes. Turn off *Sympathetic Resonance* in the Ivory preset (and *Sustain* in Pass-through). To our ears the resonance and sustain even sound better than Ivory's built-in ones — a subjective opinion, not a promise. |
| **Pianoteq** | Pass-through | Turn off Pianoteq's sympathetic resonance. |
| **Korg SX2 VST** | Host Sustain | Keeps one voice per strike; Host Sustain gives each strike its own Note Off, so restruck notes stop correctly. |
| **UVI Modern D** | Host Sustain | Works, and a restruck key no longer stays drawn down. |
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
Instruments, Korg, Pianoteq / Modartt, Yamaha CFX and Bösendorfer Imperial are trademarks
of their respective owners.
PianoToLife (formerly SympResHost) is an independent product and is not affiliated with, endorsed by or
sponsored by any of them. "Steinway D-274" designates the sampled instrument used for the
built-in resonance model.<br>
VST is a registered trademark of Steinberg Media Technologies GmbH.
Audio Unit and macOS are trademarks of Apple Inc.
</sub>
