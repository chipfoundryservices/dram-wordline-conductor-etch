# Chapter 9: Chamber Walls, Metal Deposits, Seasoning & Contamination

## Overview

Each wafer through a word-line recess chamber gives up about 12 mg of tungsten and 2 mg of TiN. Almost all of it leaves through the pump as WF₆ and TiCl₄. The small fraction that does not ends up on the chamber walls, the window, and the edge ring, as tungsten-rich films, titanium fluorides, oxyfluorides, and sulfur. Those deposits change how much fluorine the walls consume, how much power the coil couples, and how the plasma meets the wafer edge. When they build up or come off, they shift the next wafer's recess, and fragments that fall on the wafer become the most damaging defect the module can make.

This chapter covers what reaches the walls and in what amounts, why the wall state moves the recess depth, how waferless autoclean and seasoning hold the walls in a reproducible state, how edge rings shape the edge recess, and how metal and particle contamination are kept within limits.

**Learning Objectives:**
- Estimate the metal removed per wafer and the wall deposit per wafer
- Choose waferless-autoclean chemistries for tungsten, titanium, sulfur, and silicon deposits
- Model how a change in wall loss shifts the recess rate and depth
- Describe seasoning and its role in the first-wafer effect
- Explain how edge-ring material and wear shape the edge recess and step
- Set limits for metal contamination and particles, and trace their sources

---

## 9.1 What Reaches the Walls

### 9.1.1 Metal Removed per Wafer

```
Metal area on the wafer (Chapter 3.7):   113 cm²
Recess depth (array):                    85 nm
W share of the front 64%, TiN 36%

W removed:    113 cm² × 8.5×10⁻⁶ cm × 0.64 × 19.25 g/cm³ ≈ 11.8 mg
TiN removed:  113 × 8.5×10⁻⁶ × 0.36 × 5.22 g/cm³          ≈ 1.8 mg
SiO₂ removed (mask top, ≈ 3 nm over ≈ 590 cm²):           ≈ 0.4 mg
```

### 9.1.2 Where It Goes

```
Fate of etched material (illustrative):

Species             Pumped as             Deposits as                 Fraction on walls
─────────────────────────────────────────────────────────────────────────────────────
W                   WF₆ (mostly)          W-rich WFₓ, WOₓFᵧ where F is    1–3%
                                          scarce or O is present
Ti                  TiCl₄                 TiF₃/TiF₄, TiOₓFᵧ (involatile    5–15%
                                          at wall temperature)
S (from SF₆)        SF₄, SOF₂             Elemental S, SOₓFᵧ on cool      small, on cold
                                          surfaces                        spots
Si (from oxide)     SiF₄                  SiOₓFᵧ, SiOₓClᵧ films            < 1%
```

Titanium is the harder case. It leaves the wafer as TiCl₄, but in a fluorine-rich gas some of it is converted to fluorides, which stick to the walls and stay there. The fraction of titanium deposited is larger than that of tungsten, even though less titanium is etched.

### 9.1.3 Deposit Thickness

```
Inner surface area (walls, window, ring, chuck rim): ≈ 3000 cm²

W deposit at 2%:   0.24 mg per wafer → 8×10⁻⁵ mg/cm²
                   at an effective density of ≈ 8 g/cm³ → ≈ 0.10 nm per wafer
Ti deposit at 10%: TiN 1.8 mg × (47.9/61.9) × 0.10 ≈ 0.14 mg Ti per wafer,
                   as TiF₄ (× 123.9/47.9) ≈ 0.36 mg; at ≈ 2.8 g/cm³
                   → ≈ 0.43 nm per wafer

Without per-wafer cleaning: 1000 wafers → ≈ 100 nm of W-rich film and
≈ 430 nm of Ti fluoride
```

These films would flake within a few hundred wafers. Per-wafer waferless autoclean keeps them below a monolayer-scale steady state.

---

## 9.2 How the Wall State Moves the Recess

### 9.2.1 The Fluorine Balance

The fluorine density in the plasma is set by production and loss:

```
n_F = G / (k_p + k_w + k_wafer)

G:        production by dissociation
k_p:      pumping loss
k_w:      wall loss (recombination, reaction with deposits)
k_wafer:  consumption by the wafer (∝ f, the metal area fraction)

Loading factor (Chapter 3.7):  Φ f = k_wafer / (k_p + k_w)
Reference: Φ f = 0.30
```

### 9.2.2 Sensitivity to Wall Loss

```
If the wall loss rises so that (k_p + k_w) increases by 5%:

  Before:  denominator ∝ 1.00 + 0.30 = 1.30
  After:   denominator ∝ 1.05 + 0.30 = 1.35
  Rate change: 1.30 / 1.35 − 1 = −3.7%
  Depth change over 85 nm at fixed time: ≈ −3.1 nm (shallower)
```

A 5% change in wall loss is a 3 nm depth error, more than half the window. Wall loss changes with:

```
Wall condition                        Effect on F loss    Effect on recess
──────────────────────────────────────────────────────────────────────────
Fresh fluorinated YOF (after WAC)     Low                 Deeper
W-rich deposit                        High (W + F → WF₆)  Shallower
Ti fluoride deposit                   Moderate            Slightly shallower
Oxygen-rich (after O₂ clean)          Low F, adds O       Deeper W; TiN slower
                                                          → horns
Sulfur on cold spots                  Low                 Small
```

A tungsten-rich wall both consumes fluorine and releases WF₆. During one wafer's main step, the walls collect tungsten, the wall loss rises, and the rate falls slightly through the step. The effect is the same on every wafer if each starts from the same clean wall. That is the purpose of per-wafer cleaning and seasoning.

### 9.2.3 The First-Wafer Effect

```
Lot without per-wafer WAC (illustrative):
  Wafer 1 (walls freshly cleaned): z_r = 62.1 nm
  Wafer 2:                         z_r = 60.8 nm
  Wafer 3:                         z_r = 60.3 nm
  Wafers 5–25:                     z_r = 60.0 ± 0.3 nm

Lot with per-wafer WAC + season:
  All wafers:                      z_r = 60.0 ± 0.3 nm
```

The first-wafer effect also shows in the step. Freshly oxygen-cleaned walls release oxygen into the first seconds of the next main step, which slows TiN and raises the horn on the first wafer.

---

## 9.3 Waferless Autoclean and Seasoning

### 9.3.1 Cleaning Each Deposit

```
Deposit            Clean chemistry           Product        Notes
──────────────────────────────────────────────────────────────────────────────
W-rich, WOₓFᵧ      NF₃ (+ O₂)                WF₆, WOF₄      Fast; endpoint by F
                                                            emission plateau
TiFₓ, TiOₓFᵧ       BCl₃/Cl₂                  TiCl₄ (+ BF₃)  Halogen exchange: B
                                                            takes F, Ti leaves as
                                                            chloride
TiClₓ, TiN-like    Cl₂                       TiCl₄          Fast
S, C               O₂                        SO₂, CO₂       Leaves O on walls
SiOₓFᵧ             NF₃                       SiF₄           With the W step
```

Titanium fluoride cannot be cleaned with fluorine and is cleaned only slowly with chlorine alone, because TiF₄ does not react readily with Cl₂. Boron trichloride removes it by halogen exchange: boron binds the fluorine as BF₃, and titanium leaves as TiCl₄. A WAC that has only an NF₃ step slowly accumulates titanium, which is a common cause of a slow drift in recess depth over a wet-clean cycle.

### 9.3.2 The Per-Wafer Sequence

```
Reference WAC + season (no wafer on the chuck; chuck protected by low
power and short time, or a cover wafer):

Step       Gas (sccm)           p (mTorr)   Source (W)   Time / endpoint
──────────────────────────────────────────────────────────────────────────
WAC-1      NF₃ 200 / O₂ 50      30          1500         ≤ 8 s; F 703.7 nm
                                                         plateau
WAC-2      BCl₃ 100 / Cl₂ 100   20          1200         5 s
SEASON     SF₆ 40 / Cl₂ 60 /    8           700          7 s
           N₂ 20 / Ar 100
──────────────────────────────────────────────────────────────────────────
Total                                                    ≈ 20 s
```

The season step coats the walls with the same thin film the main step will create, so each wafer meets the same wall. It is short, because the film it makes is thin and the walls reach a steady state quickly.

### 9.3.3 Clean Endpoint

The NF₃ step's endpoint uses the atomic fluorine emission at 703.7 nm. While tungsten deposits are being consumed, they take fluorine and the line stays low. When the walls are clean, the line rises to a plateau. An endpoint time that grows from wafer to wafer means the deposit per wafer is growing, an early warning of a change in the main step or a cold spot.

---

## 9.4 Window and Coil

The window is the one surface where a conductive deposit changes the power (Chapter 5.5). It is also a source of particles, because it is directly above the wafer:

```
Window issue                 Cause                          Defence
──────────────────────────────────────────────────────────────────────────
Conductive W-rich film       Low window temperature,        Heated window
                             insufficient WAC               (≥ 80 °C); WAC
Ti fluoride film             NF₃-only WAC                   BCl₃/Cl₂ step
Coating erosion (Y)          Capacitive coupling through    Faraday shield
                             a damaged shield
Flakes above the wafer       Film stress after hundreds     Per-wafer WAC;
                             of nm                          wet-clean interval
```

---

## 9.5 Edge Ring and Edge Recess

### 9.5.1 Ring Material and Edge Loading

Beyond the wafer edge, the ring surface either consumes fluorine or does not. A ring that consumes fluorine acts like more metal beyond the wafer, which flattens the edge loading:

```
Ring material      F consumption     Edge z_r vs. centre (illustrative)
────────────────────────────────────────────────────────────────────
Si                 High (etched)      ≈ 0 nm (edge F depleted like the array)
SiC                Moderate           +0.8 nm
Quartz             Low                +1.6 nm (edge F-rich)
Y₂O₃-coated        Very low           +2.0 nm
```

A silicon ring is consumed and must be replaced. A quartz ring lasts longer but needs more gas-split and edge-zone correction (Chapters 7 and 8).

### 9.5.2 Ring Wear and Edge Tilt

As the ring erodes, its top falls below the wafer surface. The sheath above the ring becomes thinner than above the wafer, and the sheath edge bends at the wafer edge. Ions near the edge arrive tilted outward:

```
Ion tilt at the extreme edge (illustrative): 0.3° per 100 µm of ring height
loss below the wafer plane

Tilt 0.5° at h = 88 nm: lateral shift = 88 × tan 0.5° ≈ 0.77 nm

Effect: the TiN on the inner wall of each slot (facing the wafer centre)
is shadowed more than the outer wall → asymmetric horns, larger on one
side; seam V-notch offset toward one side
```

Edge tilt shows as a difference in horn height between the two walls of a slot, seen only in the outer 2–5 mm. It is managed by ring replacement, by adjustable ring height, or by an edge RF tuning that raises the ring's sheath.

---

## 9.6 Contamination and Particles

### 9.6.1 Particles and the Recess

A particle that lands on the wafer before or during the recess shields the metal beneath it. Where the particle covers the top of a slot, the metal beneath is not recessed and remains up to the CMP plane:

```
Particle on a word line during the recess:

   │ particle │
   ▼   ███    ▼
 ┌───┬█████┬──────────────────┐ mask top
 │   │█▓▓▓█│                  │
 │ox │ ▓▓▓ │  ← unrecessed metal stub under the particle
 │   │ ▓▓▓ │
 ├───┤ ▓▓▓ ├──────────────── Si surface
 │   │ ▓▓▓ │
 │   │▓▓▓▓▓│  ← target z_r elsewhere (60 nm)
```

The stub reaches above the silicon surface. The cap over it is thin or missing, and the storage-node or bit-line contact etch next to it lands on metal. The result is a word-line-to-contact short, a hard failure. A 40 nm particle is enough to cover one slot.

```
Particle budget (illustrative):
  Adders ≥ 40 nm during recess: target ≤ 0.005 cm⁻² (≈ 3.5 per wafer)
  Fraction landing on a WL slot in the array: ≈ 0.18 (array metal fraction
    plus overlap)
  Kill probability for a stub: ≈ 0.7 (a single-bit or row fail; most are
    repaired by redundancy)
  → ≈ 0.4 unrepaired-risk events per wafer
```

### 9.6.2 Particle Sources

```
Source                               Signature                      Fix
──────────────────────────────────────────────────────────────────────────────
Wall or window flakes (TiFₓ,         Rising adders over the         WAC (with BCl₃),
WOₓFᵧ)                               wet-clean cycle; Ti, W in EDX  wet-clean interval
Gas-line corrosion (Fe, Ni)          Fe/Ni/Cr particles; after       Line purge; Cl₂
                                     cylinder changes               moisture spec
Plasma-off settling at transitions   Clusters at the step-change     Keep plasma on
                                     position; centre-heavy         through ME → TR
Chuck rim deposits                   Edge and backside particles     Rim clean; cover-
                                                                     wafer WAC
Coating erosion (Y)                  Y in EDX; after shield or       Shield repair
                                     coil fault
```

### 9.6.3 Metal Contamination

```
Element   Source                        Limit, front side (illustrative)   Effect
───────────────────────────────────────────────────────────────────────────────────
W, Ti     Redeposition on oxide walls;  < 1×10¹⁰ cm⁻² on the gate oxide    Leakage at the
          wall flakes                   above the recess (Ch. 13)          gate edge
Y, Al     Chamber coatings              < 5×10⁹ cm⁻²                       Oxide charge
Fe, Ni,   Gas lines; CMP residue        < 5×10⁹ cm⁻²                       Generation-
Cr                                                                         recombination
                                                                           centres
Na, K     CMP, handling                 < 1×10¹⁰ cm⁻²                      Mobile charge

Backside: W, Ti < 1×10¹¹ cm⁻² (to protect later tools and furnaces)
```

Tungsten and titanium are not the fast-diffusing deep-level contaminants that iron and nickel are. Their risk is local, as a conductive or trap-rich film on the oxide next to the gate edge.

---

## 9.7 The Maintenance Cycle

```
Event                    Interval (illustrative)    Recovery
──────────────────────────────────────────────────────────────────────────
Per-wafer WAC + season   Every wafer                —
Idle recovery season     After ≥ 30 min idle        60 s waferless
Edge-ring replacement    ≈ 600–1000 RF hours        Season + edge check
                         (Si ring)
Wet clean (walls,        ≈ 2000–3000 RF hours, or   ≈ 8–12 h; season 25
window, liner)           on adder trend             wafers; qualification
                                                    (Appendix C.2)
Chuck replacement        On He-leak trend           Zone calibration
```

The wet-clean interval is set by whichever comes first: the particle trend, the clean-endpoint drift, or a recess-depth drift that APC can no longer absorb.

---

## 9.8 Summary & Key Takeaways

1. **Each wafer gives up about 12 mg of W and 2 mg of TiN.** A few percent of the W and up to 15% of the Ti end on the walls. Without per-wafer cleaning, the deposits would flake within hundreds of wafers.

2. **Wall loss moves depth.** A 5% change in wall fluorine loss changes the recess depth by about 3 nm. A tungsten-rich wall consumes fluorine and makes the recess shallower.

3. **Titanium fluoride needs BCl₃.** NF₃ removes tungsten deposits but not TiF₄. A BCl₃/Cl₂ step removes it by halogen exchange.

4. **Season every wafer.** A short season step after the clean gives every wafer the same starting wall and removes the first-wafer effect.

5. **The edge ring shapes the edge.** Ring material sets edge loading, and ring wear tilts ions at the edge, which makes horns asymmetric.

6. **Particles become shorts.** A particle on a slot leaves an unrecessed stub that the contact etch finds later. Wall flakes, corroded gas lines, and plasma-off transitions are the main sources.

---

## Study Questions

1. A product has an array efficiency of 0.60 and a recess of 88 nm. Compute the tungsten and TiN removed per wafer. With 2% of W and 10% of Ti deposited, compute the deposit per wafer on 3000 cm² of wall.

2. Using the fluorine-balance model with Φf = 0.30, compute the depth change at fixed time when the wall loss changes by +2%, −3%, and +8%. Which of these would APC feedback detect within one lot?

3. A chamber's WAC has only an NF₃ step. Over 500 wafers, the Ti fluoride film grows and raises the wall loss by 0.01% per wafer. Compute the recess drift over the 500 wafers and over a 2500-hour wet-clean cycle at 30 wafers/hour.

4. An edge ring has worn 150 µm below the wafer plane. Compute the ion tilt and the lateral shadow shift at h = 60 nm and h = 88 nm. Which wall of the slot gets the larger horn, and why?

5. The adder count for particles ≥ 40 nm rises from 3 to 10 per wafer over 400 RF hours. Using the budget of Section 9.6.1, compute the change in unrepaired-risk events per wafer. What evidence would distinguish wall flakes from gas-line corrosion?

---

**Next Chapter:** [Chapter 10: Recess Depth Control & the Gate–Junction Overlap Window](./10-recess-depth-overlap.md)

---

**Chapter 9 Development Status:** Complete  
**Version:** 1.0
