# Chapter 7: Gas Delivery, F/Cl Balance & Multi-Step Recess Recipes

## Overview

A word-line recess recipe is a short sequence of steps, each with one job. The breakthrough removes the post-CMP skins. The main recess takes the metal down. The trim levels TiN with tungsten. The post-treatment cleans the surface. Within the main step, the balance between fluorine and chlorine decides whether TiN keeps pace with tungsten, and the pressure and flow decide how strongly the rate depends on depth and on how much metal the wafer exposes. The gas system has to deliver those balances at the right moment, in the right place on the wafer, with the right purity.

This chapter treats pressure, flow, and residence time as separate knobs, the F/Cl ratio and how gas-line transients disturb it, the design of each step, center/edge gas tuning, and gas purity. It ends with the complete reference recipe and a two-step landing variant.

**Learning Objectives:**
- Separate the effects of pressure, flow, and residence time on rate, ARDE, and loading
- Compute gas-line delays and the step-start error they cause in the TiN–W step
- Design breakthrough, main, trim, and post-treatment steps from their goals
- Compute the TiN–W step before and after a trim
- Use center/edge gas split to flatten the radial recess profile
- Specify gas purity for chlorine and fluorine lines

---

## 7.1 Pressure, Flow, and Residence Time

### 7.1.1 Pressure

```
Effect of pressure in the main step (illustrative; flows, powers fixed):

  p (mTorr)              5        8        12       15
  ─────────────────────────────────────────────────────────
  ER₀ W (nm/min)         150      180      205      215
  k (ARDE)               0.030    0.035    0.044    0.050
  Ion energy (eV, fixed  66       60       53       49
    bias power)
  Collisional ion tail   3%       5%       7%       9%
  Δ_TW before trim (nm)  +3.5     +4.5     +5.5     +6.5
  Radial range z_r (nm)  3.0      2.4      2.8      3.6
```

Higher pressure raises the radical density and the open-area rate. It also raises k, because more radicals per ion are lost at the top of the slot and more ions arrive at wider angles. The ion energy at fixed bias power falls, because the ion current rises. TiN horns grow because the TiN removal in the slot corners depends partly on ions, which arrive at wider angles and are shadowed more. The reference 8 mTorr balances these effects.

### 7.1.2 Flow at Fixed Pressure

At fixed pressure, raising the total flow shortens the residence time (Chapter 5.4). That removes etch products faster and reduces the loading factor, because pumping becomes a larger share of the fluorine loss:

```
Total flow (sccm)         150      220      300      400
Residence time (ms)       170      115      85       64
Loading factor Φ          2.4      1.9      1.6      1.4
WF₆ mole fraction         2.7%     1.9%     1.4%     1.0%
Gas cost index            0.7      1.0      1.4      1.8
```

Lower Φ means less sensitivity to product area fraction and to wall state. The cost is gas consumption and pump load.

---

## 7.2 The F/Cl Balance

### 7.2.1 The Control Variable

The chlorine fraction χ = Q(Cl₂)/[Q(Cl₂) + Q(SF₆)] sets the open-area TiN–W ratio (Chapter 4.4). The reference main step runs at χ = 0.6, just on the tungsten-fast side of the crossover at 0.62. Mass flow controllers hold each flow to about ±1% of setpoint, which corresponds to Δχ ≈ ±0.003 and ΔΔ_TW ≈ ±0.6 nm over the recess. That is small, but it is per chamber and per MFC, so it enters the matching budget (Chapter 5.7.3).

### 7.2.2 Gas-Line Delays

Gases do not arrive at the chamber when the recipe step starts. Each line has a volume that must fill to the new flow:

```
Line from MFC to chamber: 3 m of 1/4" tube (ID 4.6 mm)
  Volume:          π × (2.3 mm)² × 3 m ≈ 50 cm³
  Line pressure:   ≈ 10 Torr (1330 Pa) at the chamber end
  Cl₂ flow:        60 sccm = 0.101 Pa·m³/s

  Fill time ≈ V p / Q = 5.0×10⁻⁵ m³ × 1330 Pa / 0.101 Pa·m³/s ≈ 0.66 s
```

If SF₆ and Cl₂ arrive through lines of different volume or start from different states, the first second of the main step has the wrong χ.

```
Example: SF₆ arrives 0.7 s before Cl₂ at the start of ME.
  For 0.7 s the chemistry is χ ≈ 0: W ≈ 260, TiN ≈ 40 nm/min
    W recess in that time:   0.7 × 4.33 = 3.0 nm
    TiN recess:              0.7 × 0.67 = 0.5 nm
  Extra horn ≈ 2.5 nm before the main step proper begins
```

### 7.2.3 Remedies

```
Remedy                                  Effect
──────────────────────────────────────────────────────────────────────────
Pre-flow to a divert line during the    Gas mix is at setpoint when the step
  preceding stabilization step          starts
Merge all gases into one carrier line   Same delay for all species
  close to the MFCs
Start ME with Cl₂ a fraction of a       Errs toward pullback, which the
  second earlier                        trim does not fix; not preferred
Plasma-off gas stabilization step       Adds 3–5 s but removes the transient
  between BT and ME
```

The reference recipe uses a plasma-off stabilization with pre-flow before ME, and a carrier-merged manifold.

---

## 7.3 Step Design

### 7.3.1 Breakthrough (BT)

```
Goal:      remove 1–2 nm WOₓ and 0.5–1 nm TiOₓNᵧ evenly; start all features
           together
Reference: NF₃ 20 / Ar 100 sccm, 8 mTorr, 500 W, ≈ 100 V bias (CW), 5 s
Removes:   WOₓ skin (≈ 1.5 nm) + ≈ 0.5 nm metal; mask loss ≈ 1.0 nm
```

```
Design rule: BT time ≥ 1.5 × (thickest skin / skin removal rate)

Skin removal rate ≈ 0.45 nm/s; thickest skin after 24 h queue ≈ 2.2 nm
  → BT ≥ 1.5 × 4.9 s ≈ 7 s for worst case; 5 s for the reference
    8 h queue limit (skin ≤ 1.6 nm → 3.6 s × 1.5 = 5.3 s)
```

Too short a BT leaves patches of oxide that start late. Too long costs mask and exposes the AA shoulder at the higher BT energy.

### 7.3.2 Main Recess (ME)

```
Goal:      take the conductor top to 1 nm above the target (the trim lowers
           W by ≈ 1 nm)
Reference: SF₆ 40 / Cl₂ 60 / N₂ 20 / Ar 100 sccm; 8 mTorr; 700 W source;
           60 V effective bias, synchronized pulsing 1 kHz, 50%
Time:      set by APC; nominal from the recess equation:
             start after BT at h = 4 nm, end at h = 87 nm (z = 59 nm)
             ER₀ t = (87 − 4) + (0.035/22)(87² − 4²) = 83 + 12.0 = 95.0 nm
             t = 95.0 / 3.0 ≈ 31.7 s
```

### 7.3.3 Trim (TR)

The main step leaves a TiN horn, typically 4–5 nm tall and 2 nm thick, standing above the tungsten along both walls (Chapter 11). The trim removes it from the side:

```
Goal:      remove TiN horns laterally; lower W by ≈ 1 nm; Δ_TW → 0 ± 1 nm
Reference: Cl₂ 50 / Ar 150 / O₂ 2 sccm; 15 mTorr; 600 W; ≤ 20 V bias; 6 s

Rates (illustrative):
  TiN lateral (exposed inner face of the horn):   0.6 nm/s
  TiN top-down in the 2 nm slit (once below W):   0.3 nm/s
  W (Cl₂/O₂, low bias):                           0.15 nm/s

Horn removal:  2.0 nm thick / 0.6 nm/s ≈ 3.3 s
Remaining trim time 2.7 s:
  TiN recedes below W top:  2.7 × 0.3 = 0.8 nm
  W continues down:         2.7 × 0.15 = 0.4 nm
Final:  Δ_TW ≈ −(0.8 − 0.4) ≈ −0.4 nm
W lowered during trim:  6 × 0.15 ≈ 0.9 nm  → conductor top z ≈ 60 nm ✓
```

The trim works because the horn is thin. It does not matter much whether the horn is 3 nm or 8 nm tall. The inner face is exposed along its whole height, so lateral removal finishes in about the same time. What the trim cannot fix is pullback. If the main step left TiN *below* the tungsten, the trim deepens the slit (Chapter 11).

### 7.3.4 Post-Treatment (PT)

```
Goal:      remove adsorbed F and Cl; nitride the W top; stabilize for queue
Reference: N₂ 150 / H₂ 50 sccm; 30 mTorr; 800 W; no bias; 8 s
```

### 7.3.5 Transitions

Each step change is a chance for a particle or a thermal transient. The reference recipe extinguishes the plasma between BT and ME (with pre-flow) and keeps it lit from ME into TR and from TR into PT with 1 s power ramps. The ME → TR transition with plasma on avoids exposing a freshly etched, halogen-covered surface to an unlit chamber, where heavier species settle.

---

## 7.4 A Two-Step Landing Variant

Where the window is tighter than the reference, the main step can be split:

```
Variant B:
  ME-1 (fast):    reference ME conditions to h ≈ 72 nm (z ≈ 44 nm), ≈ 25 s
  ME-2 (landing): χ = 0.64, bias 45 V, duty 35%, 10 mTorr;
                  ER₀ ≈ 85 nm/min, k ≈ 0.020; last 15 nm
                  ER₀ t = 15 + (0.020/22)(87² − 72²) = 15 + 2.2 = 17.2 nm
                  t ≈ 17.2 / 1.42 ≈ 12 s
  Rate at end ≈ 1.42 / (1 + 0.020 × 7.9) ≈ 1.23 nm/s

Benefits:  each second of time error costs 1.2 nm instead of 2.3 nm;
           lower ion energy at the gate edge; smaller horn (χ closer to
           crossover)
Cost:      ≈ 5 s more plasma time; one more transition
```

---

## 7.5 Center/Edge Gas Tuning

### 7.5.1 The Radial Fluorine Profile

On a fully patterned wafer, fluorine is consumed everywhere, but the centre is farther from the gas that flows in from the edge injectors and past the wafer edge to the pump. Without correction, the edge recesses deeper. The centre-injector fraction shifts this:

```
Centre-injector fraction vs. radial recess (illustrative, reference ME):

  Centre fraction       30%        50%        70%
  ────────────────────────────────────────────────
  z_r centre (nm)       59.0       60.0       60.8
  z_r at r = 140 mm     62.2       61.0       59.9
  Edge − centre         +3.2       +1.0       −0.9
  Δ_TW edge − centre    +0.4       +0.1       −0.2
```

The reference uses 55–60% centre flow, which brings edge − centre to near zero. The gas split moves depth far more than it moves the step, because it changes the fluorine density without changing χ much. It is the natural knob for the depth profile, while temperature is the natural knob for the step profile (Chapter 8).

### 7.5.2 Species-Selective Tuning

Some chambers inject a tuning gas (a small extra flow of one species) at the edge only. Adding 2–5 sccm of Cl₂ at the edge raises χ locally, which lowers the edge tungsten rate and raises the edge TiN rate. This is a second, independent radial knob for the step.

---

## 7.6 Gas Purity

```
Gas     Impurity of concern     Effect                         Spec (illustrative)
────────────────────────────────────────────────────────────────────────────────────
Cl₂     H₂O                     HCl in line → corrosion, Fe/Ni  ≤ 1 ppm
                                particles; O on TiN → slower
                                TiN, horns
Cl₂     O₂, N₂                  Small effect                    ≤ 10 ppm
SF₆     Air, H₂O, SOₓFᵧ         O → slower TiN                  ≤ 5 ppm H₂O
NF₃     CF₄, N₂O                Fluorocarbon on walls           CF₄ ≤ 50 ppm
Ar, N₂  H₂O, O₂                 Oxidation of TiN in PT/TR       ≤ 0.5 ppm
H₂      H₂O                     W top oxidation in PT           ≤ 1 ppm
```

Chlorine lines must be dry. Moisture in a chlorine line forms HCl, which corrodes stainless steel and releases iron and nickel particles. Those particles land in the slots and mask the recess locally (Chapter 9). Line purge procedures after every gas-cylinder change and continuous purge of idle lines keep moisture out.

---

## 7.7 The Complete Reference Recipe

```
Step   Gas (sccm)                     p        Source  Bias               Time     Plasma
                                      (mTorr)  (W)
─────────────────────────────────────────────────────────────────────────────────────────────
S1     Ar 100 / NF₃ 20                8        —       —                  4 s      off
BT     NF₃ 20 / Ar 100                8        500     ≈ 100 V, CW        5 s      on
S2     SF₆ 40 / Cl₂ 60 / N₂ 20 /      8        —       —                  4 s      off
       Ar 100 (pre-flow to divert)
ME     SF₆ 40 / Cl₂ 60 / N₂ 20 /      8        700     60 V eff., sync    APC      on
       Ar 100; centre 58%                              1 kHz, 50%         (≈ 32 s)
TR     Cl₂ 50 / Ar 150 / O₂ 2         15       600     ≤ 20 V             6 s      on (1 s ramp)
PT     N₂ 150 / H₂ 50                 30       800     none               8 s      on (1 s ramp)

ESC 50 °C (centre) / 52 °C (edge zone); He backside 15 Torr
(illustrative; a starting point for a design of experiments)
```

---

## 7.8 Summary & Key Takeaways

1. **Pressure raises rate and ARDE together.** From 5 to 15 mTorr, k rises from 0.030 to 0.050, and horns grow. 8 mTorr balances rate, ARDE, and the step.

2. **Flow sets loading.** At fixed pressure, more flow shortens residence time, lowers Φ, and reduces sensitivity to product and wall state, at a gas cost.

3. **χ is the TiN–W knob, and it must be right from the first second.** Line delays of about 0.7 s can add a 2.5 nm horn. Pre-flow and merged carrier lines remove the transient.

4. **Each step has one job.** BT clears skins, ME takes the metal down to 1 nm above target, TR removes horns laterally and lowers W by about 1 nm, and PT cleans and nitrides the surface.

5. **The trim works because horns are thin.** A 2 nm horn clears in about 3.3 s whatever its height. Pullback cannot be trimmed away.

6. **Gas split for depth, temperature for step.** The centre-injector fraction flattens the depth profile with little effect on the step. Edge Cl₂ addition and temperature zones tune the step.

---

## Study Questions

1. The main step is moved from 8 to 12 mTorr. Using the pressure table, compute the new main-step time to z_r = 60 nm (from h = 4 to 87 nm), the end rate, and the 40 nm pad z_r (use h₀ = 8 nm and the pad mask top at 29 nm). Is the move worthwhile?

2. A Cl₂ line is 5 m long instead of 3 m, and SF₆ arrives through a 1 m line. Compute the arrival delay difference and the extra horn at the start of ME, using the χ = 0 rates.

3. The trim's TiN lateral rate drops from 0.6 to 0.45 nm/s after a chamber clean. Compute the horn-removal time and the final Δ_TW for a 6 s trim, using the other rates in Section 7.3.3. Would you change the trim time?

4. Design a two-step ME for a node where the slot is 9.6 nm wide and the window is ±4 nm. ME-2 has ER₀ = 80 nm/min and k = 0.020. Choose the switch depth so that ME-2 lasts 12 s, and compute the rate at the end.

5. With the centre fraction at 50%, the edge recesses 1.0 nm deeper than the centre. A new edge ring makes the edge 1.5 nm deeper still. Using the gas-split table (assume linear), what centre fraction restores the profile?

---

**Next Chapter:** [Chapter 8: Wafer Temperature, Electrostatic Chucks & Radial Recess Uniformity](./08-temperature-esc-radial.md)

---

**Chapter 7 Development Status:** Complete  
**Version:** 1.0
