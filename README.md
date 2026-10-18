<h1 align="center">PianoToLife</h1>
<p align="center"><i>formerly SympResHost</i></p>
<p align="center"><b>Bring your VST / AU piano to life — and to realism.</b></p>
<p align="center">Replace your piano's static sympathetic resonance samples and canned pedal behaviour<br>
with one live, physically modelled string engine — from a single held key to every damper lifted.</p>
<p align="center"><b>New in 10:</b> no hosted piano needed — play your own samples with the built-in sampler.</p>

<p align="center">
  <img src="screenshot.png?v=1000" alt="PianoToLife interface" width="900">
</p>

<p align="center">
  <a href="../../releases/latest"><b>⬇ Download the latest release</b></a> ·
  macOS 14+ (Apple Silicon) · Windows 10/11 x64 · AU · VST3 · Standalone
</p>
<p align="center">
  PianoToLife is free. <a href="https://www.paypal.com/paypalme/owfrappier"><b>♥ Donate with PayPal</b></a> to support its development.
</p>

<p align="center">
  <a href="https://www.youtube.com/watch?v=aNzbEqNP4QE">
    <img src="https://img.youtube.com/vi/aNzbEqNP4QE/maxresdefault.jpg" alt="Video: 4 sampled pianos through PianoToLife" width="640">
  </a><br>
  <b>▶ Video: 4 sampled pianos through PianoToLife</b> (VSL D-274, Ivory 3, a 3-layer Steinway B, VSL 1887) — which one do you prefer?
</p>

---

## What's new in 10.0.0 — the built-in sampler

PianoToLife can now **play your own piano samples**, without a hosted piano. Switch **HOST / SAMPLER** at the top of the window: in SAMPLER, the hosted piano is set aside and PianoToLife's own sampler plays, with all of PianoToLife's engines on it (sympathetic resonance, release, una corda, pedals).

- **Your samples, a few clicks**: load your WAV / AIFF samples in **EDIT** (Kontakt-style key / velocity map). **AUTO KEY** finds each sample's note, **AUTO LAYERS** builds the velocity layers, **RECAL A4** measures the tuning and the loudness of your layers by listening to them. Fine edits per key: tune, gain, low-pass, envelope; **SELECT BY MIDI**, **UNDO / REDO**.
- **Smooth dynamics even with few layers**: **SOFT TIMBRE** gives the notes softer than a layer the spectrum of a softer strike, **HARD TIMBRE** (option) brightens the strikes above it. A map shows the step at every layer boundary (green / orange / red) and **FIX STEPS** evens it out, smoothed between neighbouring keys (one UNDO). A 3-layer Steinway B now plays like a deeply sampled piano.
- **A real piano release**: **AUTO RELEASE** sets each key's damper time by register; the release velocity counts (a slow key release lands the damper later and softer); keys without dampers ring on.
- **A native half pedal**: under a half pedal the released notes are damped by the samples themselves, continuously, with the two-part decay of a real damper (fast part + long residue); re-pedalling keeps the level reached. SAMPLER always uses Host Sustain and Una Corda Simu (both greyed there; your HOST choices are kept). Sostenuto works.
- **Large sets stream from the disk** (DFD): only the beginning of each sample stays in memory. Choose the preload, the cache and the polyphony (60…256, Max 512) in **MIX**; a disk test tells you if your drive is fast enough.
- **Microphones**: **MIX** mixes up to 5 microphone positions (level, pan, width, delay, meters); a microphone switched off is not loaded.
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
<tr><td>🎹 <b>Velocity by points</b></td><td>The velocity curve is now a line of points you can drag (double-click to add or remove a point). The CURVE knob quickly writes a smooth curve. COPY and PASTE exchange the curve as text, in the same format as Pianoteq, so you can reuse a curve made for your keyboard in Pianoteq, or share yours. Example:<br><code>Velocity = [0, 49, 66, 77, 85, 95, 102, 108, 114, 121, 127; 0, 9, 12, 19, 31, 51, 68, 88, 116, 127, 127]</code><br>The first list is the velocity you play, the second the velocity sent to the piano. Slope is gone: sessions that used Curve or Slope open with the same touch, as points.</td></tr>
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
<tr><td>🎧 <b>Full Piano = Piano Only + PianoToLife DSP Only</b></td><td>A listening selector at the top: hear your hosted piano alone, only what PianoToLife adds (resonance, release, Ambience, noises), or the whole. Comp, Reverb and Ceiling stay on; no latency. It always comes back to Full Piano (opening, ALL DEFAULT, preset, new piano).</td></tr>
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
- **Listen to each part.** Full Piano = Piano Only + PianoToLife DSP Only: hear your piano alone
  or only what PianoToLife adds, with one click.
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
    normal release (the Note-Off curves have no effect in this mode). Use **Release Decay** to
    make the release shorter or longer.
  - **Release Velocity 1-127**: for keyboards that measure how fast you release the keys
    (many Roland, Kawai, Kurzweil...) or behave in their own way. Their 1-127 range drives
    PianoToLife's dampers, release and key noise, fine-tuned with the **Note-Off Velocity Curve**
    (above 32 = firmer releases). Very low values, often sent by mistake, are read as a slow
    release, never an endless one. Check in the **MIDI Monitor**: your key releases should show
    many different values.
  - **Kawai VPC1**: made for the VPC1, whose release velocity stops around 100 and easily
    drops to 1 on a slightly slow release. Normal releases sound normal, slow ones stay
    natural. If it does not suit your playing, adjust the Note-Off Velocity Curve or go back
    to Standard.
  - **N1X or others** (Yamaha N1X and similar Yamaha hybrids): these instruments report
    the key position through polyphonic aftertouch, only while the key comes back.
    PianoToLife measures the time the key takes to return and turns it into release
    velocity (no aftertouch at all = a very fast release). It can filter the aftertouch
    and CC19 messages so the hosted piano does not receive them.
  - **Yamaha P-525**: measures the timing of the release information the P-525 sends and
    turns it into release velocity.
  - In these two modes the result **replaces the note-off velocity sent to the hosted piano**,
    shaped by the **Keyboard Note-Off Curve**. The **Note-Off Velocity Curve** only shapes
    how PianoToLife's own dampers and release respond.
- **Silent Key** (list next to SYMPATHETIC RESONANCE): a silent key press lifts the damper
  without playing a note, so the string is free to resonate (play a chord over it, or hold it
  while lifting the pedal). **≤ 1** (default), **≤ 2**, **≤ 3** = notes at that velocity or lower;
  **Disklavier / N1** = polyphonic aftertouch 127 / 0, as sent by the Yamaha AvantGrand N1 and
  Disklavier XP (all velocities play in that mode); **Off** = none. The **MIDI Monitor** button
  shows, side by side, what arrives and what is sent to the piano, with every difference in amber.
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
| **Pianoteq** | Pass-through | Turn off Pianoteq's sympathetic resonance. |
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
Instruments, Korg, Pianoteq / Modartt, Yamaha CFX and Bösendorfer Imperial are trademarks
of their respective owners.
PianoToLife (formerly SympResHost) is an independent product and is not affiliated with, endorsed by or
sponsored by any of them. "Steinway D-274" designates the sampled instrument used for the
built-in resonance model.<br>
VST is a registered trademark of Steinberg Media Technologies GmbH.
Audio Unit and macOS are trademarks of Apple Inc.
</sub>
