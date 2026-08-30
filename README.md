# Description
MATLAB code for computing passive ankle plantarflexor moment from isokinetic 
dynamometer data, including gravitational moment correction via regression on 
the Gravity-Only Region (GOR). Developed during my research work at the HUS 
Motion Laboratory, New Children's Hospital, Helsinki.

---

## Repository Contents

- `GravityOnlyRegion.mlx` — MATLAB Live Script for passive 
  moment analysis:
  - Signal filtering and ankle angle/torque extraction from raw dynamometer data
  - Cyclic averaging across repeated trials
  - Cubic polynomial fit and identification of the Gravity-Only Region (GOR)
  - Sinusoidal regression to estimate the gravitational moment component
  - Gravity-corrected passive elastic moment calculation
- `GravityOnlyRegion.html` — Rendered output (code, results, plots)

## Analysis Overview

The script:
1. Loads raw dynamometer data (ankle angle and torque), low-pass filters the 
   torque signal (4th-order Butterworth, 5 Hz cutoff), and averages it over 
   repeated cycles per angle
2. Averages ankle angle and torque data across multiple trial repetitions
3. Fits a cubic polynomial to the passive moment–angle curve to identify the 
   region used to define the Gravity-Only Region (GOR) - the 
   sub-range of the range of motion (ROM) where torque is assumed to be 
   dominated by gravitational effects
4. Fits a sinusoidal model (A₁·sin θ + A₂·cos θ) to the GOR data to estimate 
   the gravitational moment as a function of ankle angle
5. Subtracts the fitted gravitational moment from the full passive moment 
   curve, yielding the gravity-corrected passive elastic moment across the 
   entire range of motion

## How to Run

1. Download or clone this repository.
2. Open `GravityOnlyRegion.mlx` in MATLAB.
3. Update the file path in the `readtable` line to point to where you've saved 
   `Max_passive_contrex.csv` on your machine:
```matlab
   Passive_Contrex_Max = readtable('YOUR_PATH_HERE\Max_passive_contrex.csv');
```
4. Run the script section by section to reproduce the passive moment curve, 
   GOR identification, and gravity-corrected output.

Alternatively, open `GravityOnlyRegion.html` to view the 
rendered output without running MATLAB.
