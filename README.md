# 400m Hurdle Touchdown Calculator

A professional-grade tool for coaches and athletes to analyse 400m hurdles races in real time. Enter touchdown splits as they come in and get instant projections, velocity profiles, and sectional analysis.

**Live tool:** [your-username.github.io/400m-hurdle-calculator](https://your-username.github.io/400m-hurdle-calculator)

---

## Features

**Calculator tab**
- Enter cumulative touchdown times for H1–H10 and finish
- Instantly see each hurdle interval, vs-target delta (green/red), and estimated 100m / 200m / 300m split checkpoints
- Target splits panel shows what times are required at each hurdle for your goal
- Projected finish time appears from H2 onward, updating with every entry
- Partial run support — enter as few or as many hurdles as you have
- Velocity profile chart (m/s per segment) for actual vs target
- 100m sectional breakdown: 0–100, 100–200, 200–300, 300–finish, plus 1st/2nd 200m and differential
- Save up to 20 runs in browser storage, reload at any time
- Optional stride pattern input per hurdle

**Pace guide tab**
- Enter any target time and see the full split-by-split breakdown
- 100m / 200m / 300m checkpoints highlighted
- Interval change column shows where the athlete is expected to slow (red) or maintain (green)
- Velocity profile for the target pace

**Coverage**
| Gender | Range | Based on |
|--------|-------|---------|
| Men | 45.0 – 70.0s | SpeedEndurance table + IAAF biomechanical studies |
| Women | 49.0 – 80.0s | SpeedEndurance table |

Targets outside the calibrated range are flagged and extrapolated.

---

## Methodology

Pacing profiles are derived from the [SpeedEndurance.com](https://speedendurance.com) touchdown time tables, cross-validated against:
- IAAF World Championships Berlin 2009 biomechanical analysis (DLV)
- London Diamond League 2017 biomechanical profiles

**Hurdle positions used:** H1=45m, then 35m spacing (H2=80m, H3=115m … H10=360m), finish=400m.

**100m checkpoints** are interpolated via segment velocity:
- 100m: H2 (80m) → project +20m using H2→H3 velocity
- 200m: H5 (185m) → project +15m using H5→H6 velocity
- 300m: H8 (290m) → project +10m using H8→H9 velocity

**Projection model:** For each hurdle, solves the quadratic `t_i = (base_ratio + drift × (finish − midpoint)) × finish` for `finish`. This is target-independent — the projection only changes when actual split times are entered, not when the target is adjusted.

**H1 note:** The SpeedEndurance table records H1 clearance times (leading foot over hurdle), not touchdown times. The H1 ratio is corrected from real race data. H1 projection is suppressed — too much variance from block reaction and acceleration phase to be useful.

---

## Usage

No installation needed. It's a single HTML file with no build step.

### Run locally
```
open index.html
```
or just drag `index.html` into a browser.

### Deploy to GitHub Pages
1. Fork or clone this repository
2. Go to **Settings → Pages**
3. Set source to **main branch / root**
4. Your URL will be `https://your-username.github.io/400m-hurdle-calculator`

---

## Contributing

Issues and PRs welcome. Areas that could be improved:
- Women's H1 ratio validation against more real race data
- Run comparison view (load a saved run as overlay)
- Athlete/event metadata on saves
- 400m flat mode

---

## Credits

- Pacing structure: [SpeedEndurance.com](https://speedendurance.com) 400m hurdle touchdown tables
- Biomechanical validation: DLV/IAAF Berlin 2009 World Championships analysis
- Chart.js for velocity profile visualisation

---

## Licence

MIT — free to use, adapt, and share.
