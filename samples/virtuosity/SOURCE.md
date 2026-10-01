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
| `kick` | `kick_snon_vl3_rr1` | 1.0 s (cap) |
| `kick-accent` | `kick_snon_vl4_rr1` | 1.0 s (cap) |
| `snare-ghost` | `snare_center_vl9` | 0.6 s (cap) |
| `snare` | `snare_center_vl26` | 0.42 s |
| `snare-accent` | `snare_center_vl36` | 0.42 s |
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

In the take names, `vl` is the velocity layer (higher is louder) and `rr` the round-robin take. The kit has two toms, so there is no separate mid-tom sample.
