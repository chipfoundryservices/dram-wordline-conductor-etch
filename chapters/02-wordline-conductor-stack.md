# Chapter 2: The Word-Line Conductor Stack — Gate Oxide, TiN, Tungsten Fill & CMP

## Overview

The recess etch does not choose its starting point. It inherits a slot lined with gate oxide, a TiN liner of a given thickness and composition, a tungsten core with a seam down its middle, and a surface left by CMP with its own dishing, erosion, oxide skin, and residue. Each of these sets part of the result. The gate oxide sets the slot width and so the ARDE. The TiN thickness sets how much of the surface is the slow-etching metal. The tungsten microstructure sets where the seam lies and how the surface roughens. The CMP sets the height from which the recess starts.

This chapter describes the incoming stack layer by layer, the variation each layer brings, and how that variation becomes recess-depth and surface-shape variation. It ends with the incoming specification the recess etch needs.

**Learning Objectives:**
- Compute the slot width from the trench width, the grown oxide, and the deposited oxide, in the silicon and in the hard mask
- Describe ALD TiN composition and how chlorine, oxygen, and density affect its etch rate
- Explain how CVD tungsten fills a narrow slot, why it leaves a seam, and why its resistivity is high
- Describe tungsten CMP, dishing, erosion, and the starting height of the recess
- Compare CMP-then-recess with etchback-only flows
- State the incoming specification for the recess etch

---

## 2.1 The Gate Oxide and the Slot

### 2.1.1 Why the Gate Oxide Is Thick

The cell transistor's gate oxide is much thicker than a logic gate oxide. The word line swings from about −0.3 V to about 2.9 V, so the oxide must carry 3.2 V for the life of the part, and the oxide at the gate edge must keep the GIDL field low. The reference stack uses an equivalent thickness of 3.5 nm of SiO₂, made in two parts:

```
Reference gate dielectric:
  Radical (in-situ steam) oxidation:   2.5 nm grown on silicon walls
  ALD SiO₂:                            1.0 nm deposited everywhere
  Total on silicon walls:              3.5 nm
  On SiO₂ hard-mask walls:             1.0 nm (ALD only)
```

Radical oxidation is used because it grows nearly the same thickness on all silicon crystal planes and rounds the top corners of the AA. Both matter in a trench whose walls run in many crystal directions as they wrap the tilted islands. The ALD layer adds thickness without consuming more silicon from the 14 nm islands.

### 2.1.2 Silicon Consumed and Oxide Added

Thermal oxidation consumes 0.44 nm of silicon for each nanometre of oxide grown. The grown oxide extends outward from the original wall by 0.56 of its thickness and into the silicon by 0.44:

```
Grown oxide 2.5 nm:
  Silicon consumed per wall:  0.44 × 2.5 = 1.1 nm  (wall moves into the Si)
  Oxide protruding inward:    0.56 × 2.5 = 1.4 nm  (into the trench)
ALD oxide 1.0 nm:             1.0 nm inward

Etched trench opening (before oxidation):  W₀ = 15.8 nm
  Si–oxide interface after oxidation:      W₀ + 2 × 1.1 = 18.0 nm  (= w_t)
  Conductor slot in the silicon:           W₀ − 2 × (1.4 + 1.0) = 11.0 nm  (= w_s)
```

The AA silicon between word-line trenches loses 1.1 nm per wall, which the word-line trench etch must already have budgeted.

### 2.1.3 The Slot in the Hard Mask

The 30 nm SiO₂ hard mask above the silicon surface does not oxidize further. Only the ALD layer forms on its walls:

```
Slot in the hard mask:  W₀ − 2 × 1.0 = 13.8 nm
Slot in the silicon:    11.0 nm

Shoulder at the silicon surface: each wall steps inward by 1.4 nm
```

```
Slot cross-section near the Si surface:

 z=−30 ─┐    13.8 nm    ┌─  mask top (CMP plane)
        │               │   1.0 nm ALD on SiO₂ mask
        │               │
 z=0   ─┘└┐   11.0 nm  ┌┘└─ Si surface; 1.4 nm shoulder per side
          │            │    3.5 nm oxide on Si
          │            │
```

The first 30 nm of recess runs in a 13.8 nm slot, and the rest runs in an 11 nm slot. The W core in the mask region is 9.8 nm wide. The shoulder becomes important in two places: transport (the upper slot is easier to etch through, Chapter 3) and the TiN, which forms a short step over the shoulder that the trim must clear (Chapter 11).

### 2.1.4 Oxide Variation

```
Source of variation                     Typical 3σ        Effect on slot w_s
────────────────────────────────────────────────────────────────────────────
WL trench CD (etch + litho)             ±1.2 nm           ±1.2 nm
Grown oxide thickness                   ±0.15 nm          ±0.13 nm
ALD oxide thickness                     ±0.05 nm          ±0.10 nm
Combined (RSS)                                            ±1.2 nm
```

The trench CD dominates. Chapter 3 shows that each nanometre of slot width changes the final recess depth by about 0.9 nm.

---

## 2.2 The TiN Liner

### 2.2.1 What the TiN Does

```
Function                     Requirement
───────────────────────────────────────────────────────────────────────────
Work function                ≈ 4.6 eV (mid-gap side of n-type); sets V_T
                             with the channel doping
Barrier during W CVD         Stops WF₆ and HF from attacking the gate oxide
                             and silicon; ≥ 1.5 nm continuous
Adhesion and nucleation      Gives the W nucleation layer a surface to grow on
Conductor                    Carries part of the current (≈ 8% in the reference)
```

### 2.2.2 ALD TiN Composition

ALD TiN is grown from TiCl₄ and NH₃ at about 400–450 °C. It is never pure stoichiometric TiN:

```
Typical composition of 2 nm ALD TiN (illustrative):
  N/Ti ratio              1.0–1.1
  Cl (residual)           0.3–1.0 at.%
  O (from air exposure    2–8 at.% (higher near both interfaces)
     and the oxide)
  Density                 4.8–5.1 g/cm³ (bulk TiN 5.22)
  Resistivity             120–200 µΩ·cm at 2 nm (≈ 25 µΩ·cm bulk)
```

Each of these affects the recess. Oxygen turns part of the TiN into TiOₓNᵧ, which etches more slowly in chlorine. Low density etches faster. A cooler or shorter ALD cycle leaves more chlorine and less density. A 10% change in TiN etch rate, which a deposition drift can cause, is enough to create a 3 nm TiN–W step over a 90 nm recess if the recipe has no trim (Chapter 11).

### 2.2.3 TiN Thickness and the Metal Fraction of the Surface

The recess front is made of two TiN strips and one tungsten strip:

```
Surface composition of the recess front (in the silicon):
  TiN:  2 × 2.0 nm = 4.0 nm  of 11.0 nm → 36%
  W:              7.0 nm  of 11.0 nm → 64%

In the hard mask (13.8 nm slot):
  TiN:  4.0 nm of 13.8 → 29%; W: 9.8 nm → 71%
```

TiN is a third of the front. It is also on the outside, against the oxide wall, where ion flux is lower and redeposition is higher than at the slot centre (Chapter 3).

---

## 2.3 The Tungsten Fill

### 2.3.1 Nucleation and Bulk Growth

CVD tungsten cannot grow directly on TiN with good adhesion and uniform nucleation using WF₆ and H₂ alone. The fill is done in two stages:

```
Stage              Chemistry                         Thickness   Character
─────────────────────────────────────────────────────────────────────────────────
Nucleation layer   WF₆ + B₂H₆ (or SiH₄), pulsed      1.0–2.0 nm  Amorphous or β-W;
(ALD-like)         at ≈ 300 °C                                   high ρ; B or Si
                                                                 incorporated
Bulk fill          WF₆ + 3H₂ → W + 6HF               to closure  α-W columnar
                   at 300–400 °C                                 grains
```

In a 7 nm core, a 1.5 nm nucleation layer on each side leaves only 4 nm for bulk growth. Much of the core is nucleation layer with boron, which has higher resistivity and etches somewhat faster in fluorine than α-W. Fluorine-free tungsten processes (from WCl₅ or WCl₆ precursors) and boron-free nucleation are used in some flows to lower resistivity and avoid fluorine reaching the gate oxide.

### 2.3.2 Conformal Fill and the Seam

The tungsten grows inward from both TiN walls at the same rate. The two growth fronts meet on the slot centreline and leave a **seam**:

```
Conformal fill of a near-vertical slot (cross-section):

  t = 0           t = 1           t = 2 (closure)
 │      │        │▓    ▓│        │▓▓▓┆▓▓▓│
 │      │        │▓    ▓│        │▓▓▓┆▓▓▓│   ┆ = seam
 │      │        │▓    ▓│        │▓▓▓┆▓▓▓│
 │      │        │▓    ▓│        │▓▓▓┆▓▓▓│
 └──────┘        └▓▓▓▓▓▓┘        └▓▓▓▓▓▓▓┘

If the slot narrows toward the top (re-entrant), the top closes first
and leaves a void below:
                 │▓▓▓┆▓▓▓│ ← closed at top
                 │▓▓  ○ ▓▓│ ← void
                 │▓▓▓┆▓▓▓│
```

The seam is a grain-boundary plane where columnar grains from opposite walls meet, often with nanometre-scale voids along it. It has a lower density than the grains on either side, and it is a fast path for fluorine. Its shape depends on the slot profile:

```
Slot profile                       Seam character
──────────────────────────────────────────────────────────────────────
Slightly tapered (wider at top)    Tight seam, closes bottom-up; best
Vertical                           Continuous seam along full height
Bowed or re-entrant (narrower      Void below the narrow point; seam
  at top, e.g. at the shoulder)    open above it
```

The reference slot narrows from 13.8 nm in the mask to 11 nm in the silicon at the shoulder. That is a widening upward, not re-entrant, so it does not trap a void, but the seam at the shoulder may be less tight where the fronts from the wider slot meet. The recess removes the mask region entirely, so this matters mainly for the first seconds of the etch (Chapter 12).

### 2.3.3 Grain Size and Resistivity

```
Resistivity of narrow W (illustrative):
  Bulk α-W:                          5.3 µΩ·cm
  Electron mean free path λ (W):     ≈ 15 nm (estimates range 15–19 nm)
  Grain size in a 7 nm core:         ≈ 3–6 nm (limited by the core)

  Grain-boundary and surface scattering raise ρ to ≈ 15–30 µΩ·cm
  Reference (with nucleation layer and seam):  ρ_W = 22 µΩ·cm
```

The high resistivity of narrow tungsten is why molybdenum and ruthenium, with shorter mean free paths and the option of thinner or no liner, are studied for future word lines (Chapter 14).

### 2.3.4 Fluorine in the Tungsten

WF₆-based fill leaves fluorine in the tungsten and at the W–TiN interface, typically 10¹⁸–10¹⁹ cm⁻³ in the bulk and more along the seam. During the recess the fluorine is released at the surface. During later anneals, some of it diffuses through the TiN into the gate oxide. A little fluorine at the oxide–silicon interface passivates traps; more creates fixed charge and weakens the oxide. The recess etch adds its own fluorine to the oxide above the conductor (Chapter 13).

---

## 2.4 Tungsten CMP and the Starting Height

### 2.4.1 The Overburden

After fill, tungsten and TiN cover the whole wafer. The reference overburden on the field is about 60 nm of W on 2 nm of TiN on 1 nm of ALD oxide on the 30 nm SiO₂ hard mask. The overburden over the array is slightly lower, because some of the deposited tungsten went into the slots.

### 2.4.2 The CMP Process

Tungsten CMP uses an oxidizing slurry (H₂O₂, often with an iron catalyst) that converts the tungsten surface to a soft oxide, and silica or alumina abrasive that removes it. A second, more selective step clears the TiN and stops on the SiO₂ hard mask.

```
Polish stage          Removes                         Ends on
────────────────────────────────────────────────────────────────────────
W bulk                W overburden at high rate       Near the TiN
TiN / barrier         TiN, residual W, and a few      SiO₂ hard mask
                      nm of SiO₂ (controlled
                      selectivity)
Buff / clean          Slurry, oxidized W              —
```

### 2.4.3 Dishing and Erosion

Two pattern effects set the height of the metal at the start of the recess:

```
Dishing:  the metal surface sits below the surrounding oxide, because the
          pad bends into each metal opening. Grows with the opening width.
Erosion:  the oxide in a dense array is thinned more than isolated oxide,
          because the array removes more material overall.

Representative values (illustrative):
  Feature                         Dishing    Erosion of mask    Metal top vs.
                                  (nm)       (nm)               field mask top
  ───────────────────────────────────────────────────────────────────────────
  Array (11 nm slots, 34 nm       3          2                  −5 nm
    pitch, 32% metal)
  SWD pads (40 nm wide)           8          1                  −9 nm
  Isolated WL end (11 nm)         2          0                  −2 nm
  Field (no metal)                —          0                  0
```

So the recess does not start at a single height. The array starts 5 nm below the field mask top, and the pads start 9 nm below. The recess target is set from the silicon surface, so what matters is how far each feature's metal top is above z = 0:

```
Starting metal-top height above the Si surface:
  Array:  30 − 5 = 25 nm   → remaining recess to z_r = 60:  85 nm
  Pads:   30 − 9 = 21 nm   → remaining recess:               81 nm
```

The reference value R = 90 nm is measured from the as-deposited mask top. In the array the etch must actually remove 85 nm of metal, starting from a surface 25 nm above the silicon. The two descriptions are used side by side in this book. Chapter 3 computes etch time from the array's starting height.

### 2.4.4 Within-Wafer and Wafer-to-Wafer Variation

```
Source                                    3σ (illustrative)
────────────────────────────────────────────────────────────
Hard-mask thickness (deposition)          ±1.2 nm
Erosion (CMP radial, pad life)            ±1.8 nm
Dishing (CMP, slurry lot)                 ±0.8 nm
Combined starting height (RSS)            ±2.3 nm
```

This variation passes straight into the recess depth unless it is measured and fed forward (Chapter 15). It is the largest single term in the depth budget of Chapter 10.

### 2.4.5 The Post-CMP Surface

```
Surface feature                Origin                    Effect on recess
─────────────────────────────────────────────────────────────────────────────
WOₓ skin (1–3 nm)              Slurry oxidizer; air      Slow start; must be
                               after polish              broken through (Ch. 4.5)
TiOₓNᵧ at TiN top              Slurry and air            Slow TiN start → horn
Slurry particles               Incomplete clean          Micromasks → local
                                                         under-recess
Iron, potassium residue        Catalyst, clean           Contamination
Seam corrosion                 Slurry enters seam        Seam already open at
                                                         start (Ch. 12)
Organic residue (inhibitors)   Slurry additives          Slow, non-uniform start
```

The oxide skin grows with time in air. A queue-time limit between CMP clean and recess (typically a few hours to one day) keeps it predictable.

---

## 2.5 CMP-Then-Recess Versus Etchback-Only

### 2.5.1 Etchback-Only

Some flows skip the tungsten CMP and remove the overburden with the same plasma that does the recess. The etch first clears about 60 nm of tungsten from the field, then about 2 nm of TiN, and then continues down into the slots.

```
Etchback-only sequence:
  1. Bulk W etch on the field (≈ 60 nm), endpoint when the field clears
     (optical emission falls as the exposed W area collapses; Ch. 15)
  2. TiN clear on the field (Cl-based)
  3. Timed recess from the mask top to z_r
```

### 2.5.2 The Trade-Off

```
Property                         CMP + recess              Etchback only
─────────────────────────────────────────────────────────────────────────────────
Starting-height variation        ±2.3 nm (Section 2.4.4)   ±3–4 nm: overburden
                                                           ±3% of 60 nm plus
                                                           clearing-time spread
Pattern effects at start         Dishing, erosion          Overburden thinner over
                                                           the array; field clears
                                                           at different times
Endpoint available               No (constant metal area)  Yes, at field clear
Metal on the hard mask after     None                      Must be cleared fully;
                                                           any W left bridges WLs
Cost                             CMP step + clean          One longer etch
Chamber load                     ≈ 90 nm of W in slots     ≈ 60 nm of W over the
                                 (16% of wafer area)       whole wafer first
Typical use                      High-volume DRAM          Older nodes; some
                                                           development flows
```

The etchback-only flow removes several times more tungsten per wafer, which loads the plasma and the chamber walls much more (Chapter 9). Its endpoint at field clear is an advantage, but the clearing time varies across the wafer, and the slots in the first-cleared regions start their recess earlier. **The reference process in this book uses CMP followed by recess.**

---

## 2.6 Geometries the Recess Must Handle

```
Feature                      Slot width    Starting height    Fraction of
                             (nm)          above Si (nm)      metal area
──────────────────────────────────────────────────────────────────────────
Array WL (in Si)             11.0          25                 ≈ 92%
Array WL (in mask region)    13.8          —                  —
First and last array WLs     11–13         26                 ≈ 2%
Dummy WLs at array edge      11–15         26                 ≈ 2%
SWD landing pads             40            21                 ≈ 3%
WL end caps and straps       15–25         23                 ≈ 1%
Test structures, marks       ≥ 100         15–20              < 1%
```

The array dominates the metal area, so it dominates the chemistry of the plasma. The pads and the edges are few, but each one carries a word line, and each must also meet its own depth limit. The array edge is also where patterning error is largest, because the SAQP lines end there (Book #26, Chapter 2).

---

## 2.7 The Incoming Specification

```
Parameter                          Target          Limit (illustrative)
──────────────────────────────────────────────────────────────────────────
WL trench CD at Si surface (w_t)   18.0 nm         ± 1.2 nm (3σ)
Gate oxide on Si (EOT)             3.5 nm          ± 0.15 nm
TiN thickness                      2.0 nm          ± 0.15 nm
TiN O content                      ≤ 5 at.%        ≤ 8 at.%
W fill                             Seam ≤ 1 nm     No voids above z = 100 nm
                                   open
Hard-mask thickness (field)        30 nm           ± 1.2 nm
Array erosion + dishing            5 nm            ± 2.0 nm
Pad dishing                        8 nm            ≤ 12 nm
Metal residue on field             None            None (WL–WL bridge)
Queue time CMP → recess            ≤ 8 h           ≤ 24 h
Post-CMP particles                 —               Within budget
```

---

## 2.8 Summary & Key Takeaways

1. **The slot is 11 nm in the silicon and 13.8 nm in the mask.** Radical oxidation consumes 1.1 nm of silicon per wall and protrudes 1.4 nm. The ALD oxide adds 1 nm everywhere. The mask walls get only the ALD layer.

2. **TiN is a third of the recess front.** It is ALD-grown with oxygen and chlorine in it, and its etch rate depends on composition. A 10% change in TiN rate can make a 3 nm step.

3. **The tungsten core has a seam.** Conformal growth from both walls meets on the centreline. The seam is less dense than the grains and gives fluorine a fast path downward.

4. **Narrow tungsten is resistive.** A 7 nm core with nucleation layer and seam has a resistivity near 22 µΩ·cm, about four times bulk.

5. **CMP sets the starting height.** Erosion and dishing put the array metal 5 nm and the pads 9 nm below the field mask top. Starting-height variation (±2.3 nm, 3σ) is the largest term in the depth budget unless fed forward.

6. **CMP-then-recess is the reference flow.** Etchback-only gives an endpoint at field clear but more starting variation and much heavier metal loading.

---

## Study Questions

1. A trench is etched with W₀ = 15.0 nm. The radical oxide grows 2.8 nm and the ALD oxide is 0.8 nm. Compute the Si–oxide interface width, the conductor slot in the silicon, the slot in the hard mask, and the shoulder step per side.

2. For the slot of Question 1 with 1.8 nm TiN, compute the W core width in the silicon and the TiN fraction of the recess front. Would you expect a larger or smaller TiN–W step than in the reference process for the same rate mismatch? Explain.

3. A 1.5 nm boron-containing nucleation layer has ρ = 100 µΩ·cm, and the bulk α-W in the core has ρ = 15 µΩ·cm. For a 7 nm core with nucleation on both walls, compute the effective resistivity, treating the layers as parallel conductors.

4. The CMP of a new slurry lot increases array erosion by 1.5 nm and pad dishing by 3 nm. Compute the new starting heights above the silicon for the array and the pads. If the recess time is not changed, how does z_r move in each? (Use a local rate of 2.3 nm/s near the end of the recess.)

5. An etchback-only flow has 60 nm of field overburden with ±3% (3σ) thickness non-uniformity, and an open-area W rate of 180 nm/min. Compute the spread in field-clear time across the wafer. How much extra recess do the earliest-cleared slots receive, at a slot rate of 2.6 nm/s?

---

**Next Chapter:** [Chapter 3: Metal Recess Physics in Narrow Slots](./03-recess-etch-physics.md)

---

**Chapter 2 Development Status:** Complete  
**Version:** 1.0
