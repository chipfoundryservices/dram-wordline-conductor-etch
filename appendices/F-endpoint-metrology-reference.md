# Appendix F: Endpoint & Metrology Reference

Signals, methods, sampling, and control limits for the DRAM word-line recess module. Values are illustrative.

---

## F.1 In-Situ Signals by Step

```
Step     Signal                          Use                          Typical behavior
──────────────────────────────────────────────────────────────────────────────────────────────
S1, S2   Pressure, flows                 Gas exchange complete         Settle within 3 s;
                                                                       pre-flow on divert
BT       W 400.9 nm                      Skin cleared (monitor)        Rises over 2–4 s, then
                                                                       flat; late rise = thick
                                                                       WOₓ
         Bias V_pp                       Ion energy                    Flat ± 2%
ME       F 703.7 / Ar 750.4              Free F (rate predictor)       Flat ± 2%; falls with
                                                                       loading and wall loss
         Cl 837.6 / Ar 750.4             χ check                       Flat ± 2%
         W 400.9, Ti 498–500 nm          Etch-product level            Flat; level ∝ rate ×
                                                                       metal area
         Reflectometry (scribe grating)  Target depth (if fitted)      Continuous depth;
                                                                       stop at predicted value
         Bias V_pp, pulse readback       Ion energy; pulsing on        Square-wave pattern;
                                                                       CW = fault
TR       Ti 498–500 nm                   Horn removal activity         Falls over ≈ 3 s as
                                                                       horns clear
PT       H 656.3, N₂ 337.1               Gas, plasma state             Flat
WAC-1    F 703.7 nm                      W deposit cleared             Rises to plateau;
                                                                       endpoint time trended
WAC-2    Ti 498–500 nm, B 249.7 nm       Ti fluoride cleared            Ti falls to baseline
SEASON   F/Ar, Cl/Ar                     Wall state                     Same as ME baseline
```

---

## F.2 Etchback-Only Field-Clear Endpoint

```
Before clear: metal area fraction f = 1.0;  after clear: f = 0.16
F density ratio (Φ = 1.9):  (1 + 1.9) / (1 + 0.30) = 2.9 / 1.3 ≈ 2.2

Endpoint: F 703.7 / Ar rises ≈ ×2 over the clearing period; call at
the knee of the derivative; overetch timed from the call
```

---

## F.3 Post-Etch Metrology

```
Method          Parameter                  Precision      Accuracy vs. TEM   Sampling
                                           (3σ)
──────────────────────────────────────────────────────────────────────────────────────────
OCD (in-die)    z_r (array), mask          ±0.3 nm        ±0.7 nm            2 wafers/lot,
                thickness, slot width                                        13 sites
OCD (scribe)    z_r (grating), for         ±0.3 nm        ±1.0 nm            same
                reflectometry correlation
XRF             W areal mass → h_eff       ±1%            ±1 nm               1 wafer/lot
STEM + EDX      W top, TiN top, Δ_TW,      ±0.3 nm        Reference           Weekly/chamber,
                notch, oxide, residue                                         3 sites
AFM             Pad recess, dishing        ±0.3 nm        ±0.5 nm             1 wafer/lot (pads)
E-beam VC       Stubs (pre-cap); voids,    Detection      —                   1 wafer/lot,
                shorts (post-cap)          ≥ 1 slot                           sampled area
Ellipsometry /  WOₓ thickness on blanket   ±0.1 nm        —                   Queue excursions
XPS             monitors
```

---

## F.4 Electrical Test Structures

```
Structure                         Measured                 Reference      Limit (illustrative)
──────────────────────────────────────────────────────────────────────────────────────────────
WL resistance line (52 µm)        R_SWL                    13.9 kΩ        ≤ 15.0 kΩ
GIDL array (cell transistors)     I_D at V_G = −0.3 V,     1.0 (norm.)    ≤ 2.0 (norm.)
                                  V_D = 1.1 V, 95 °C
GIDL activation energy            E_a of I_D(T)            —              Shift > 0.1 eV =
                                                                          TAT increase
Cell I_on array                   I_on at V_G = V_PP       1.0 (norm.)    ≥ 0.92
WL–BC comb                        Leakage at 3 V           < 1 pA         No shorts
WL–WL comb                        Leakage at 3 V           < 1 pA         No shorts
WL–BC capacitance                 C per µm                 Ref.           ± 3%
WL contact chain (SWD pads)       R per contact            Ref.           ≤ 1.3 × ref.
```

---

## F.5 APC Parameters

```
Parameter              Value                  Source
──────────────────────────────────────────────────────────────────────
t_ref                  31.7 s                 Reference recipe (h 4 → 87)
r_end                  2.34 nm/s              Recess equation
∂z_r/∂H₀               1.0                    By construction (C.6)
∂z_r/∂w                0.87                   ARDE model (C.6)
EWMA λ                 0.3                    Chapter 15.5.3
Feed-forward input     9-site post-CMP OCD    Every wafer
Time clamp             ± 3 s from t_ref       Hold lot if exceeded
Reset                  Wet clean, ESC change  Chapter 15.5.4
```

---

## F.6 Control Limits (Illustrative)

```
Parameter                    Target     Warning         Control (hold)
──────────────────────────────────────────────────────────────────────
z_r array (lot mean)         60.0       ± 1.5 nm        ± 2.5 nm
z_r radial range             ≤ 3.0      > 3.5 nm        > 4.5 nm
z_r pad (AFM)                71.9       > 73.5 nm       > 75 nm
Δ_TW (STEM audit)            −0.4       outside ± 1.5   outside ± 2.0, or
                                                        any veil
Notch depth (STEM)           ≤ 5        > 6 nm          > 8 nm
Mask loss (OCD)              3.2        > 4.0 nm        > 5.0 nm
F/Ar in ME (per wafer)       baseline   ± 3%            ± 5%
WAC-1 endpoint time          baseline   + 15%           + 30%
Adders ≥ 40 nm               ≤ 3.5      > 6             > 10 per wafer
```

---

## F.7 Measurement-to-Cause Map

```
Observed                                      Measurement that confirms the cause
──────────────────────────────────────────────────────────────────────────────────
Mean depth shift (all chambers)               Post-CMP OCD (incoming); CD-SEM (CD)
Mean depth shift (one chamber)                F/Ar trend; WAC endpoint; blanket rate
Radial shift                                  He leak per zone; edge-ring hours;
                                              gas-split readback
Depth OK, R_SWL up                            XRF (W remaining); STEM notch
Depth OK, GIDL up                             STEM Δ_TW (horns); GIDL E_a (TAT)
WL–BC shorts up                               E-beam VC after cap; STEM for slits
                                              and stubs; particle adders
Row-parity pattern in bitmaps                 CD-SEM odd/even WL CD; OCD by line type
```

---

**Appendix F Version:** 1.0
