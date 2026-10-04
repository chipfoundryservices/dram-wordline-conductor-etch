# Chapter 14: Advanced Schemes — Dual-Work-Function Gates, New Metals, ALE, 4F² & 3D DRAM

## Overview

The reference process is a single TiN/W recess with a ±5 nm window. Each generation narrows the slot and the window while the recess depth stays about the same (Chapter 1.5.3). The industry has several responses. It can change what the top of the word line is made of, so that a higher gate edge costs less GIDL. It can change the metal, so that a thinner conductor still has low resistance. It can change how the recess is done, trading time for control. Or it can change the cell, so that the word line is no longer a rod in a slot. Each response brings its own conductor etch.

This chapter covers the dual-work-function word line and its polysilicon recess, molybdenum and ruthenium word lines and their recess chemistries, atomic-layer, thermal, and wet recess options, the word lines of 4F² vertical-channel DRAM, and the word lines of 3D DRAM.

**Learning Objectives:**
- Explain how a dual-work-function word line widens the overlap window and what it costs
- Compute the metal and polysilicon recess targets and times for a dual-work-function stack
- Compare W, Mo, and Ru word lines in resistance, recess chemistry, and integration risk
- Choose between plasma, ALE, thermal, and wet recess for a given window and throughput
- Describe the metal spacer and recess etches of a 4F² vertical-channel word line
- Describe the lateral word-line recess in 3D DRAM and its tier-to-tier uniformity problem

---

## 14.1 Dual-Work-Function Word Lines

### 14.1.1 The Idea

GIDL depends on the band bending at the gate edge, which depends on the voltage difference between the gate and the drain and on the gate's work function. Tungsten/TiN has a work function near 4.6–4.7 eV, which the cell transistor needs over the channel to keep its threshold high and its off-state leakage low. Near the junction, a lower work function would reduce the band bending and the GIDL. A **dual-work-function (DWF)** word line uses TiN/W in the lower part, over the channel, and n⁺ polysilicon (work function about 4.1 eV) in the upper part, next to the junction.

```
Dual-work-function word line (cross-section across the WL):

 z=0   ──┤ox│        SiN cap          │ox├──
         │  │                         │  │
 z=52  ──┤  ├─────────────────────────┤  ├──  poly top (gate edge)
         │  │   n⁺ polysilicon         │  │   ≈ 23 nm tall
 z=62    │  │  (x_j inside this part)  │  │
 z=75  ──┤  ├──┬───────────────────┬──┤  ├──  metal top
         │  │Ti│        W          │Ti│  │
         │  │N │                   │N │  │   TiN/W over the channel
 z=140 ──┤  └──┴───────────────────┴──┘  ├──
```

### 14.1.2 What It Buys

```
Illustrative: n⁺ poly lowers the gate-edge band bending by ≈ 0.5 V, which
lowers GIDL at a given overlap by about one decade.

With the reference GIDL slope (one decade per 8 nm, Chapter 1.4.1),
the GIDL limit moves from Δ_ov = +7 nm to about +15 nm.

Overlap window (reference TiN/W):  −3 to +7 nm   (10 nm wide)
Overlap window (DWF, illustrative): −3 to +15 nm  (18 nm wide)
```

The gate edge can sit higher, overlapping the junction well, which also lowers the series resistance at the junction and improves write current. The wider window makes the poly recess easier to control than the single metal recess. The passing-gate coupling for row hammer is also lower, because the passing word line's top is low-work-function polysilicon.

### 14.1.3 Two Recesses

```
DWF sequence:
  1. TiN/W fill, CMP (as reference)
  2. METAL RECESS to z_m = 75 nm (deeper than the reference 60 nm)
  3. Optional barrier on the metal top (thin TiN or WN) to stop W–Si
     reaction in later anneals
  4. n⁺ poly deposition (in-situ P-doped) to fill the slot; poly CMP or
     etchback to the mask top
  5. POLY RECESS to z_p = 52 nm
  6. SiN cap (as reference)
```

### 14.1.4 The Deeper Metal Recess

```
Metal recess to z_m = 75 nm: final hole depth 28 + 75 = 103 nm, A = 9.4

  ER₀ t = (103 − 3) + (0.035/22)(103² − 3²) = 100 + 16.9 = 116.9 nm
  t ≈ 39 s
  ∂z_m/∂w = 1.15 nm per nm (vs. 0.87 for the reference)
```

The metal top in a DWF word line sits below the junction, under the polysilicon. Its exact height matters less for GIDL, but it still sets the work-function boundary. That boundary must lie below the junction (so the metal is not next to the n⁺) and above the channel's upper end (so the low-work-function poly does not lower the threshold). A window of about ±6 nm is typical.

### 14.1.5 The Polysilicon Recess

```
Poly recess (HBr/Cl₂/O₂, from the Polysilicon Etch companion volume),
illustrative:
  Open-area n⁺ poly rate ER₀ = 150 nm/min (2.5 nm/s); k ≈ 0.03
  From h₀ = 3 nm to h = 28 + 52 = 80 nm:
  ER₀ t = 77 + (0.03/22)(80² − 9) = 77 + 8.7 = 85.7 nm → t ≈ 34 s

Selectivity poly : SiO₂ in HBr-based chemistry > 100 → wall oxide loss
  negligible
```

The poly recess has its own issues:

```
Issue                         Cause                              Remedy
───────────────────────────────────────────────────────────────────────────────
Poly seam / void              Conformal poly fill of the 11 nm   Seam-tolerant
                              slot leaves a seam (as for W)      chemistry; anneal
Doping-dependent rate         n⁺ poly etches faster in Cl;       Control in-situ
                              dopant segregation near the top    doping profile
Poly residue on the walls     Poly on the oxide wall above the   Short isotropic
(stringers)                   recess (lags like TiN horns)       trim (HBr/NF₃)
Breakthrough on the metal     If poly recess overshoots, metal   Large margin
                              top is exposed                     (52 vs 75 nm)
```

### 14.1.6 The Cost

```
Effective conductor height falls from 108 to 93 nm (metal top at 75 nm):
  h_eff = 0.29 × 65 + 0.71 × 105 ≈ 93 nm
  R_SWL ≈ 13.9 kΩ × 108 / 93 ≈ 16.1 kΩ  (+16%; above the 15 kΩ limit of the
  reference)
The polysilicon adds negligible conduction (≈ 40 kΩ/µm).

Two recess etches per wafer → twice the chambers (Chapter 5.7.2)
```

The DWF gate trades word-line resistance and an extra module for a wider GIDL window. The resistance penalty is one of the main reasons molybdenum and ruthenium are studied (Section 14.2).

### 14.1.7 Other Work-Function Options

Instead of polysilicon, a low-work-function metal layer or a TiN top doped with a work-function-lowering element (such as lanthanum diffused from a cap) can provide the same effect with lower resistance and no polysilicon recess. These options move the problem from the etch to the deposition and anneal, but they still rely on a controlled metal recess to place the work-function boundary.

---

## 14.2 Molybdenum and Ruthenium Word Lines

### 14.2.1 Why Change the Metal

```
Resistivity in narrow conductors (illustrative):

Metal   ρ bulk     Electron mean     ρ in a ≈ 7–11 nm      Liner needed?
        (µΩ·cm)    free path (nm)    conductor (µΩ·cm)
──────────────────────────────────────────────────────────────────────────
W       5.3        ≈ 15–19            ≈ 22 (with nucleation  TiN 2 nm + nucleation
                                     layer, 7 nm core)      layer
Mo      5.3        ≈ 14               ≈ 15–18 (10–11 nm,     Thin or none
                                     liner-free)
Ru      7.1        ≈ 6.6              ≈ 12–15 (11 nm,        None (adhesion layer
                                     liner-free)            ≤ 0.5 nm at most)
```

The main gain is not the bulk resistivity. It is removing the 2 nm TiN liner and the high-resistivity nucleation layer, so the whole 11 nm slot can carry current through a better-grained metal:

```
Liner-free Ru filling the full 11 nm slot, h_eff = 108 nm, ρ = 14 µΩ·cm:
  A = 11 × 108 ≈ 1190 nm²
  R′ = 1.4×10⁻⁷ / 1.19×10⁻¹⁵ ≈ 118 Ω/µm  (vs. 267 Ω/µm reference)
  R_SWL ≈ 6.1 kΩ  (−56%)
```

That margin pays for a DWF gate's resistance penalty with room to spare.

### 14.2.2 Recess Chemistry

```
Metal   Volatile products                   Recess chemistry (illustrative)
──────────────────────────────────────────────────────────────────────────────────
W       WF₆ (bp 17 °C)                      F-based + Cl for TiN (reference)
Mo      MoF₆ (bp 34 °C); Mo oxychlorides    F-based like W; or Cl₂/O₂, where Mo
        more volatile than W oxychlorides   oxychlorides leave at lower T than W's
Ru      RuO₄ (bp ≈ 40 °C)                   O₂ plasma with a little Cl₂; oxygen
                                            radicals form RuO₄; no fluorine needed
```

Ruthenium recess is a different process. It runs in oxygen, which does not etch SiO₂ at all. Its selectivity to the gate oxide is excellent, and there is no fluorine to attack the oxide, the seam, or the silicon behind a pinhole. Its difficulties:

```
Ru-specific issue                Notes
──────────────────────────────────────────────────────────────────────────────
RuO₂ (involatile) vs. RuO₄       Insufficient O or too little Cl leaves RuO₂ residue
                                 and a rough surface
RuO₄ toxicity                    Exhaust abatement; chamber-open safety
RuO₄ redeposition                RuO₄ decomposes to RuO₂ on warm surfaces: walls,
                                 window; particles
Ru CMP                           Hard, chemically inert; CMP before recess is
                                 difficult and costly
Cost and supply                  Precursors and target material
```

Molybdenum is closer to tungsten: it etches in fluorine with similar chemistry, and its oxychlorides offer a chlorine/oxygen path at lower temperature. Its main integration concern is oxidation. MoOₓ forms readily in air and in oxidizing cleans, so the queue time to the cap and the post-recess clean chemistry must be tighter than for tungsten.

### 14.2.3 No TiN, No Step

A liner-free word line has no TiN–W step. The whole slot is one metal, and Chapter 11's horns and slits disappear. In their place, the interface between the metal and the gate oxide becomes the gate edge directly, and any metal left on the wall above the recess (the counterpart of a horn) is now the main metal itself. A thin adhesion layer, if used, can still lag and form a small horn.

---

## 14.3 Recess Methods Compared

```
Method                  Directional?   ARDE          TiN–W balance        Throughput       Seam
─────────────────────────────────────────────────────────────────────────────────────────────────────
Pulsed plasma (ref.)    Yes            k ≈ 0.035     Horn + trim          ≈ 30 WPH         N₂-protected
Plasma + quasi-ALE      Yes            k ≈ 0.01 in   Good                 ≈ 22–25 WPH      Good
  landing                              landing
Plasma ALE (full)       Yes            ≈ 0           EPC ratio            ≈ 4 WPH          Good
Thermal ALE (oxidize /  No (isotropic, ≈ 0 (if       Chemistry-specific   Low; batch       Opens the seam
  convert / remove)     self-limiting) saturated)                         possible         per cycle
Remote plasma (radicals No             Weak          Poor (F-only)        High             Opens the seam
  only)
Wet recess (TiN)        No             None          Selective to TiN     Batch            Attacks W, seam
                                                     if formulated
```

Isotropic methods have no ARDE and no damage, and they suit the lateral recesses of 3D DRAM (Section 14.5). In a buried word line with a seam, they open the seam. Directional plasma recess with a quasi-ALE landing remains the best compromise for planar 6F² arrays.

---

## 14.4 Word Lines in 4F² Vertical-Channel DRAM

### 14.4.1 The Cell

A 4F² cell puts the transistor channel vertically in a silicon pillar. The bit line runs at the bottom, the storage node sits on top, and the word line wraps the pillar, on one side, two sides, or all around, in the middle:

```
4F² vertical-channel transistor (cross-section across WLs, schematic):

        SN           SN           SN        ← storage nodes on top
      ┌────┐       ┌────┐       ┌────┐
      │ n⁺ │       │ n⁺ │       │ n⁺ │      top junction
      │    │▓     ▓│    │▓     ▓│    │
      │ Si │▓ WL  ▓│ Si │▓ WL  ▓│ Si │      ▓ metal word line (TiN or
      │    │▓     ▓│    │▓     ▓│    │        TiN/W), formed as a spacer
      │ n⁺ │       │ n⁺ │       │ n⁺ │      bottom junction
   ═══╧════╧═══════╧════╧═══════╧════╧═══   buried bit line
```

### 14.4.2 Two Edges, Both Etched

The word line now has a top edge, facing the storage-node junction, and a bottom edge, facing the bit-line junction. Both overlaps matter, as in Chapter 10, but each comes from a different step:

```
Edge          Set by                                         Analogue in 6F²
───────────────────────────────────────────────────────────────────────────────
Bottom edge   Height of a dielectric pedestal etched back    —
              between pillars before metal deposition
              (an oxide recess)
Top edge      Recess of the metal spacer from the top         The buried WL
              (a vertical-film recess)                        recess
Separation    Spacer etch that clears metal from the trench   —
of WLs        bottom between pillar rows
```

### 14.4.3 The Metal Spacer Etch

```
Illustrative geometry:
  Gap between pillar rows (after gate oxide):  16 nm
  TiN deposited conformally:                   5 nm on each sidewall
  Remaining gap:                               6 nm
  TiN at the gap bottom to clear:              5 nm (on the pedestal)

Spacer etch: anisotropic Cl₂/BCl₃ (or Cl₂/Ar) at low energy
  Must clear 5 nm at the bottom of a 6 nm wide, ≈ 80 nm deep gap
  (A ≈ 13) without thinning the 5 nm sidewall film
  Overetch 50% on the bottom → lateral loss on the sidewall must be
  < 0.5 nm → lateral:vertical rate ratio < 0.2
```

The spacer etch separates word lines on opposite sides of the gap. Any metal left at the bottom bridges them, a word-line-to-word-line short. Too much lateral etch thins the word line and raises its resistance, which is already high for a 5 nm TiN film without tungsten.

### 14.4.4 The Top-Edge Recess

After the spacer etch, the gap is filled with dielectric and the metal spacer is recessed from the top to set the top edge. The metal is now a vertical film 5 nm thick between the gate oxide and the fill dielectric, recessed down a 5 nm wide slot of its own:

```
Recess of a 5 nm metal spacer to 40 nm below the pillar top:
  Slot width 5 nm; final A ≈ 8; k for Cl-based TiN recess ≈ 0.04
  Depth sensitivity to spacer thickness: ∂z/∂t_TiN ≈ 1.5 (higher than
  the buried-WL case because the slot is half as wide)
```

The 4F² word line therefore has two recess-like etches on two edges, both in narrower slots than the 6F² buried word line. Its overlap budget is tighter, and its depth sensitivity to film thickness is higher.

---

## 14.5 Word Lines in 3D DRAM

### 14.5.1 Stacked Horizontal Cells

3D DRAM stacks horizontal 1T1C cells in tiers, built from a silicon/silicon-germanium superlattice or deposited channel layers. In one family of designs, the word lines are horizontal plates formed in each tier by replacing sacrificial layers with metal through a vertical slit, as in the 3D NAND replacement gate (Book #24). The metal deposited into the lateral cavities must then be separated tier from tier by a **lateral recess** from the slit:

```
Lateral word-line recess from a slit (schematic, 3 of N tiers):

   slit │                        │
        │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓  │  ← metal deposited into the tier cavity
        │                        │     and on the slit wall
  ══════╡════════════════════════   dielectric between tiers
        │◄ recess ►▓▓▓▓▓▓▓▓▓▓▓▓  │  ← after lateral recess: metal pulled
  ══════╡════════════════════════     back 15 nm from the slit wall,
        │◄ recess ►▓▓▓▓▓▓▓▓▓▓▓▓  │     tiers electrically separated
```

### 14.5.2 The Uniformity Problem

The recess is isotropic (thermal, wet, or remote-plasma) because it must etch sideways into each tier. The etchant must travel down a slit that may be micrometres deep. Tiers near the top see more etchant than tiers near the bottom:

```
Illustrative: 64 tiers, slit 2.0 µm deep, 120 nm wide (A ≈ 17)
Lateral recess target 15 nm ± 2 nm on every tier

  Etchant depletion along the slit (transport + consumption by
  N tier faces): top-to-bottom flux ratio 1.3 for a moderately
  reactive etchant
  → top tiers recess ≈ 30% more than bottom tiers at fixed time
  → 15 nm bottom target means ≈ 19.5 nm at the top: outside ± 2 nm
```

The remedies are those of 3D NAND word-line separation: a less reactive etchant at higher dose (closer to self-limiting), cyclic dose–purge sequences that let the etchant reach the bottom before reacting, and thermal ALE chemistries that saturate on every tier. The lateral recess also faces its own TiN–W balance, now in a horizontal cavity, and the same seam problem: the metal fills each cavity from top and bottom faces and leaves a horizontal seam in the middle of each tier, which an isotropic etchant follows.

### 14.5.3 Vertical Word Lines

In other 3D DRAM designs, the word line is a vertical conductor running through the tiers, with horizontal channels around it. Its etch problems are closer to those of the 3D NAND memory hole and the vertical gate: a deep, narrow, uniform metal fill and a top-recess that must not vary along a micrometre-deep line. These designs move the word-line conductor etch toward the high-aspect-ratio problems of Books #23–25.

---

## 14.6 Roadmap

```
Generation / cell        Word-line conductor          Conductor etch focus
──────────────────────────────────────────────────────────────────────────────────────
6F² 1x–1b                TiN/W, single recess         Pulsed plasma + trim (reference)
6F² 1b–1c                TiN/W + n⁺ poly (DWF)        Deeper metal recess + poly recess;
                                                      quasi-ALE landing
6F² 1c–1d                Mo or Ru (liner-free) ± DWF  New chemistries (F/Cl/O for Mo;
                                                      O₂/Cl₂ for Ru); no TiN–W step
4F² VCT                  TiN (± W) spacer gate        Metal spacer etch + top-edge recess;
                                                      two edges
3D DRAM                  Lateral metal plates or      Isotropic lateral recess across
                         vertical gates               tiers; HAR metal etch
(illustrative; timing and choices vary by manufacturer)
```

---

## 14.7 Summary & Key Takeaways

1. **A low-work-function top widens the window.** n⁺ polysilicon at the gate edge lowers GIDL by about a decade, moving the overlap limit from +7 to about +15 nm.

2. **The DWF gate costs a second recess and resistance.** The metal recesses to 75 nm (39 s, ∂z/∂w = 1.15), and R_SWL rises about 16%.

3. **New metals buy back resistance.** Liner-free Ru in the full slot gives about 118 Ω/µm, less than half the reference, and removes the TiN–W step. Ru recesses in oxygen as RuO₄. Mo etches like W but oxidizes readily.

4. **Isotropic methods trade ARDE for the seam.** ALE, thermal, and wet recess remove ARDE and damage but open seams. Plasma with a quasi-ALE landing remains the planar-array compromise.

5. **4F² word lines have two etched edges.** A metal spacer etch separates word lines, and a recess sets the top edge in a 5 nm slot with high thickness sensitivity.

6. **3D DRAM turns the recess sideways.** Lateral recess from a deep slit must be the same on every tier, which drives self-limiting, cyclic chemistries.

---

## Study Questions

1. A DWF word line is designed with the poly top at 50 nm and x_j = 62 nm. Using the DWF window of −3 to +15 nm, compute the overlap and the margin on each side. If the metal top is at 75 ± 6 nm, what is the minimum polysilicon height?

2. Compute the time to recess the metal to z_m = 72 nm and 78 nm for the reference array, and the width sensitivity at each. Which target would you choose if the trench CD is ±1.5 nm (3σ)?

3. For a liner-free Mo word line with ρ = 17 µΩ·cm filling the 11 nm slot, compute R′ and R_SWL for the reference recess and for a DWF metal recess to 75 nm. Does Mo restore the 15 kΩ limit for the DWF gate?

4. A 4F² word-line spacer etch must clear 5 nm of TiN at the bottom of a 6 nm gap 80 nm deep. If the bottom etch rate is 30% of the open-area rate because of ARDE and the lateral rate on the sidewall is 8% of the open-area rate, compute the sidewall loss for a 50% overetch. Is it within 0.5 nm?

5. In a 64-tier 3D DRAM lateral recess, the top-to-bottom etchant flux ratio is 1.3 with continuous exposure. A cyclic process saturates each tier at 1.5 nm per cycle, with 95% saturation at the bottom tier. Compute the number of cycles for a 15 nm recess and the top-to-bottom difference.

---

**Next Chapter:** [Chapter 15: Endpoint, Metrology & Advanced Process Control](./15-endpoint-metrology-apc.md)

---

**Chapter 14 Development Status:** Complete  
**Version:** 1.0
