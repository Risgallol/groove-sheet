# Where these samples come from

All 18 files are made from **Virtuosity Drums** by Versilian Studios and Karoryfer Samples:
https://github.com/sfzinstruments/virtuosity_drums

Licence: CC0 1.0 (public domain dedication). No attribution is required; this note is kept so the source can be traced.

## How each file was made

For every hit, the kick-mic, snare-mic and overhead-mic recordings of the same take were summed at equal level, which is the mix the library's own "basic kit" uses. Then:

- one gain (−3.75 dB) was applied to all files, so the loudest hit (`snare-accent`) peaks at −1 dBFS and the natural balance between drums is kept;
- the start was trimmed to 1 ms before the attack (for `hihat-foot`, to just before the "chick");
- the tail was cut where it falls 56 dB below the hit's own peak, or at the length cap below, and faded out;
- output is stereo, 48 kHz, 16-bit FLAC.

| File | Source take (`Samples/<mic>/<drum>/<mic>_…`) | Length |
| --- | --- | --- |
| `kick` | `kick_snoff_vl4_rr2` (see below) | 0.42 s |
| `kick-accent` | `kick_snoff_vl4_rr4` (see below) | 0.42 s |
| `snare-ghost` | `snare_center_vl9` | 0.6 s (cap) |
| `snare` | `snare_center_vl30` (see below) | 0.42 s |
| `snare-accent` | `snare_center_vl36` (see below) | 0.42 s |
| `snare-cross-stick` | `snare_crossstick_vl12` | 0.7 s (cap) |
| `hihat` | `hh_closed_vl3_rr1` | 0.48 s |
| `hihat-accent` | `hh_closed_vl4_rr1` | 0.31 s |
| `hihat-open` | `hh_open_vl3_rr1` | 2.5 s (cap) |
| `hihat-foot` | `hh_pedal_vl2_rr1` | 0.5 s (cap) |
| `ride` | `ride_ride_vl2_rr1` | 4.0 s (cap) |
| `ride-accent` | `ride_ride_vl3_rr1` | 4.0 s (cap) |
| `crash` | `crash_crash_vl2_rr1` | 6.0 s (cap) |
| `crash-accent` | `crash_crash_vl3_rr1` | 6.0 s (cap) |
| `tom-high` | `htom_center_vl11` | 1.11 s |
| `tom-high-accent` | `htom_center_vl16` | 0.88 s |
| `tom-floor` | `ltom_center_vl11` | 1.82 s |
| `tom-floor-accent` | `ltom_center_vl16` | 1.68 s |

The two kick files are processed further, because the recorded kick has almost no sound above 120 Hz and disappears on small speakers. Each is the hardest hit with the snare wires off, blended 50/50 with a soft-saturated (tanh) copy, lifted +4 dB at 180 Hz and +6 dB at 3.5 kHz, peak-matched to the unprocessed hit, then given a shorter tail: full level for 70 ms, an exponential decay (time constant 70 ms) after that, cut at 0.42 s with a 20 ms fade.

The `snare` and `snare-accent` files are shaped for more snap: the first few milliseconds lifted (up to +5 dB, fading out with a 6 ms time constant), EQ of +2 dB at 200 Hz, −2 dB at 900 Hz and +5 dB at 4.5 kHz, and a shorter ring (full level for 50 ms, then an exponential decay with a 90 ms time constant), cut at 0.42 s. Their levels are set so the normal hit plays 3 dB louder than the first version, with the accent the same 4.4 dB above it.

In the take names, `vl` is the velocity layer (higher is louder) and `rr` the round-robin take. The kit has two toms, so there is no separate mid-tom sample.
