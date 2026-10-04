# Appendix D: Process Windows & Lookup Tables

Starting recipes, sensitivities, and lookup tables for the reference DRAM word-line recess. All values are illustrative and consistent with the models of Chapters 3, 4, 7, 8, 10, and 11. Use them as starting points for a design of experiments, not as qualified conditions.

---

## D.1 Reference Recipe

```
Step   Time     p        Source   Bias                Gases (sccm)                ESC
                (mTorr)  (W)                                                      (°C, C/E)
────────────────────────────────────────────────────────────────────────────────────────────
S1     4 s      8        —        —                   Ar 100, NF₃ 20              50 / 52
BT     5 s      8        500      ≈ 100 V, CW         NF₃ 20, Ar 100              50 / 52
S2     4 s      8        —        —                   SF₆ 40, Cl₂ 60, N₂ 20,      50 / 52
                                                      Ar 100 (pre-flow)
ME     APC      8        700      60 V eff., sync     SF₆ 40, Cl₂ 60, N₂ 20,      50 / 52
       (≈ 32 s)                   1 kHz, 50%          Ar 100; centre 58%
TR     6 s      15       600      ≤ 20 V              Cl₂ 50, Ar 150, O₂ 2        50 / 52
PT     8 s      30       800      none                N₂ 150, H₂ 50               50 / 52
────────────────────────────────────────────────────────────────────────────────────────────
After each wafer: WAC-1 (NF₃/O₂, ≤ 8 s, F endpoint) + WAC-2 (BCl₃/Cl₂, 5 s)
                  + SEASON (ME chemistry, 7 s)

Outputs: array z_r 60.0 nm; 40 nm pad z_r 71.9 nm; pre-trim Δ_TW +4.5 nm;
post-trim Δ_TW −0.4 nm; notch ≈ 5 nm; mask loss ≈ 3.2 nm; wall oxide loss
≤ 0.22 nm; shoulder loss ≈ 1.3 nm
```

---

## D.2 Main-Step Sensitivities

```
Knob (change)                 z_r (nm)    Pre-trim Δ_TW   k          Mask loss   Notch
──────────────────────────────────────────────────────────────────────────────────────────
Time +1 s                     +2.3        +0.1            —          +0.07 nm    ≈ 0
χ +0.05                       −6.4*       −10             −0.002     −0.2 nm     ↓
Pressure +4 mTorr             +7.6*       +1.0            +0.009     +0.3 nm     ↑
Source +100 W                 +2.5        +0.3            +0.002     +0.3 nm     ↑
Bias +10 V                    +1.5        −0.4            +0.003     +0.8 nm     ↓
Duty 50 → 70%                 +10.4*      +0.5            +0.008     +0.6 nm     ↓
N₂ 20 → 0 sccm                +2.0        +0.3            ≈ 0        ≈ 0         ↑↑
Wafer +1 K                    +0.47       −0.74           ≈ 0        ≈ 0         ↑
Centre gas +10%               −0.4 (ctr), ≈ −0.15 (S)     —          —           —
                              edge−ctr −1.0
* at fixed time; APC would shorten the step
```

---

## D.3 Time-to-Depth Lookup (Array, Reference ME)

```
ER₀ = 3.0 nm/s, k = 0.035, w = 11 nm, h₀ = 3 nm, mask top 28 nm above Si

t (s)    z_r (nm)    Rate (nm/s)
────────────────────────────────
 5       −10.5       2.84
10         3.4       2.73
15        16.8       2.63
20        29.7       2.53
25        42.2       2.45
30        54.3       2.38
32.4      60.0       2.34
(rate = 3.0 / (1 + 0.035 h/11) with h = z_r + 28)
```

---

## D.4 Width and k Lookup

```
z_r (nm) at the reference exposure (ER₀ t = 97.3 nm), h₀ = 3 nm:

Slot w (nm)   k = 0.020   k = 0.035   k = 0.050
────────────────────────────────────────────────
 9.8          63.7        58.9        54.8
10.4          64.1        59.5        55.5
11.0          64.5        60.0        56.2
11.6          64.9        60.5        56.8
12.2          65.2        61.0        57.4
(k changed with the exposure unchanged; APC re-centres the 11.0 nm value.
The spread across the column, not its centre, is what k controls.)

∂z_r/∂w:  k = 0.020 → 0.55;  0.035 → 0.87;  0.050 → 1.14 nm/nm
```

---

## D.5 Overlap Window

```
x_j = 62 nm. GIDL: one decade per 8 nm of overlap. I_on: −4% per nm of
underlap.

z_r (nm)   Δ_ov    GIDL (rel.)   I_on (rel.)   R_SWL (kΩ)   Retention   tWR
                                                            fails       fails
──────────────────────────────────────────────────────────────────────────────
53         +9      7.5           1.00          13.0         6.5×        1.0×
55         +7      4.2           1.00          13.3         3.4×        1.0×
57         +5      2.4           1.00          13.5         2.0×        1.0×
60         +2      1.0           1.00          13.9         1.0×        1.0×
63         −1      0.42          0.96          14.3         0.8×        1.5×
65         −3      0.24          0.88          14.6         0.75×       4×
67         −5      0.13          0.80          14.9         0.75×       20×

DWF (n⁺ poly top): GIDL limit moves from Δ_ov = +7 to ≈ +15 nm
```

---

## D.6 Depth Budget

```
Contributor (3σ)                       Raw (nm)    With feed-forward (nm)
────────────────────────────────────────────────────────────────────────
CMP starting height                    2.3         1.0
Etch within wafer                      1.5         1.5
Etch wafer to wafer                    1.0         1.0
Chamber to chamber (residual)          0.7         0.7
Slot width via ARDE                    1.05        1.05
Local top surface                      0.8         0.8
Breakthrough start                     0.5         0.5
RSS z_r                                3.3         2.6
+ junction x_j (2.0) → RSS overlap     3.9         3.3     (window ± 5)
```

---

## D.7 Step and Trim Window

```
Pre-trim Δ_TW (nm)   Post-trim Δ_TW (6 s trim)   Verdict
──────────────────────────────────────────────────────────────
+9                   −0.4                         OK
+4.5 (reference)     −0.4                         OK
+2                   −0.4                         OK
+0.5                 −1.1                         Marginal (over-trim)
−2                   −2.9                         Fail (slit; cap void risk)

Pre-trim target ≥ 3σ (1.5 nm) + 1.0 nm margin = 2.5 nm; reference 4.5 nm
Trim time window: 4.5–8 s (≤ 4 s leaves tall horns if lateral rate drops
25%; ≥ 8 s deepens slits to > 1.5 nm)
```

---

## D.8 Pad and Feature Lookup

```
Same exposure (ER₀ t = 97.3 nm), k = 0.035:

Feature                       w (nm)   Mask top   h₀ (nm)   z_r (nm)
─────────────────────────────────────────────────────────────────────
Array WL                      11       28         3         60.0
First real WL at array edge   11       28.8       2.8       59.0
Isolated WL end               11       30         2         57.2
WL strap / end cap            20       29         4         64.6
SWD pad (30 nm)               30       29         8         70.6
SWD pad (40 nm, reference)    40       29         8         71.9
Pad limit                                                   ≤ 75
```

---

## D.9 Dual-Work-Function Variant

```
Metal recess:  to z_m = 75 nm (hole 103 nm, A = 9.4), ≈ 39 s at reference
               ME; ∂z_m/∂w = 1.15 nm/nm; window ± 6 nm
Poly recess:   n⁺ poly, HBr/Cl₂/O₂, ER₀ ≈ 150 nm/min, k ≈ 0.03;
               to z_p = 52 nm, ≈ 34 s
R_SWL:         ≈ 16.1 kΩ (h_eff ≈ 93 nm)
Overlap window: −3 to ≈ +15 nm
```

---

**Appendix D Version:** 1.0
