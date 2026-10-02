# PianoToLife 9.0.2 — formerly SympResHost

**A new name, transitions that breathe like a real grand, and a new look.**

### ✨ SympResHost is now PianoToLife

Same plug-in, same sound engine, a name that says what it does: **bring your piano to life**.
Your sessions and presets open exactly as before (the plug-in keeps its identity in your DAW); it now appears
as **PianoToLife** in your plug-in lists. Your models, presets and settings stay where they are, and the installer replaces the old SympResHost files.

Every pedal transition was measured against a modelled concert grand, with the same MIDI performance, and
tuned step by step: half pedal, slow pedal-ups, quick re-pedals, pedal catch in every register.

### 🦶 Half pedal, closer than ever

- **A held half pedal now decays naturally**, in one smooth slope, instead of dropping quickly and then
  hanging on a plateau.
- **The resonance follows the dampers through the whole half-pedal zone**: lightly brushed near the top,
  more and more damped as the pedal comes up. No more "full sustain" plateau at mid-pedal.
- **Slow pedal-ups no longer bump**: the hand-over from your piano's note to PianoToLife's string is now
  seamless, and starts at the right moment.

### 🎯 Re-pedalling and pedal catch

- **Quick re-pedals keep their energy** like a real piano: the dampers take a moment to come down from
  their lifted position, and what survives one dip survives the next ones better.
- **Pedal catch follows the register**: crisper in the treble, fuller in the bass and middle, as on a real
  instrument.

### 🔁 Repeated notes in the pedal (Host Sustain)

- **A note restruck under the pedal now replaces its previous strike**, like a hammer striking a string that
  is still ringing: fast repeats no longer pile up, diminuendos follow what you play, and the sound clears
  naturally after the last strike (measured against a modelled grand). Every Note On still gets its Note Off.
- The former behaviour stays available as **Host Sustain (stacked)**; sessions saved with earlier versions
  keep it.

### 🎹 Upright key noise

Under KEY NOISE, choose **GRAND** or **UPRIGHT**: the same wooden sound, with the upright action's own
timing and balance (a quicker, drier return, livelier on short and repeated notes), measured on a modelled
upright.

### 🎚 Better defaults

- **Resonance Level:** the new 0 dB is 3 dB richer. Sessions and presets saved with earlier versions are
  recalled 3 dB lower on the knob, so they sound exactly the same.
- **Key Noise and Pedal Noise:** quieter by default (Key Noise −8 dB, Pedal Noise −12 dB at 0 dB, for strings,
  mechanism and damper felts alike). Earlier sessions are recalled higher on the knobs, so they sound the same.
- **Pedal Damper Curve: 32** (linear) by default (was 8): the setting all of this was tuned with.
- **Inharmonicity: 50 ct** by default (was 80 ct). Existing sessions and presets keep their value.
- **Half Pedal Damping: 25 to 95** by default (was 26 to 102), the range all the half-pedal tuning was done with. Existing sessions and presets keep their values.
- **Pedal pressed after the attack, keys still held** (syncopated pedalling): the sympathetic resonance now blooms in about one second, a little under what a pedal pressed before the attack gives (and less the later the pedal comes), more on chords than on single notes. Before, it added almost nothing (or swelled slowly in the bass). Re-pedalling after staccato notes (Pedal Catch) is unchanged. New **Held** control (next to Pedal Catch, dB, 0 = Pianoteq-like) to make this bloom stronger or softer.
- **Harmonic Balance** (formerly Mode Weights) is now a centred control: **0 is the recommended balance**
  (the former 10 %, was 30 % by default), towards −100 all harmonics even and brighter, towards +100 the
  colour of a string struck by its hammer. Double-click to come back to 0. Saved sessions keep their sound.

### 🎨 Interface themes

Choose your colours in the title bar: **NOIR & OR** (default), **GRAPHITE**, **NOIR & ROUGE**, or
**CLASSIC** (the former look). Your choice is remembered for every instance. Sound and settings are not
affected.

### Download

| | |
|---|---|
| **macOS 14+ (Apple Silicon)** | `PianoToLife-9.0.2-macOS-AppleSilicon.pkg` — signed and notarized (AU, VST3, Standalone) |
| **Windows 10/11 x64** | `PianoToLife-9.0.2-Windows-Setup.exe` (VST3, Standalone) — or the `.zip` |

Updating from an earlier version: just install over it. Your sessions and presets open as before.

Enjoying PianoToLife? It is free — a coffee on [PayPal](https://www.paypal.com/paypalme/owfrappier)
keeps it moving. ♥
