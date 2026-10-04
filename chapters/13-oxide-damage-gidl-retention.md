# Chapter 13: Gate-Oxide Integrity, Plasma Damage, GIDL & Retention

## Overview

As the recess front moves down the slot, it uncovers the gate oxide above it. That oxide, 3.5 nm thick on each wall, stays in the finished cell. It lies between the nitride cap and the silicon of the storage-node junction, and its lower few nanometres sit right above the gate edge, where the field that drives gate-induced drain leakage is highest. Whatever the plasma does to it is never removed. Thinning, fluorine and chlorine uptake, trapped charge from ultraviolet light and charging, and metal left on its surface all become leakage paths or reliability risks at the most sensitive point in the cell.

This chapter covers how long each part of the oxide is exposed, how much it thins, what the halogens and photons do to it, why charging is a local and transient risk, how metal redeposits on it, how these effects become GIDL, retention tails, and reliability loss, and how a recess recipe is designed with damage in mind.

**Learning Objectives:**
- Compute the exposure time of the gate oxide as a function of depth
- Estimate oxide thinning on the walls and at the AA shoulder
- Describe fluorine, chlorine, and hydrogen incorporation and their consequences
- Estimate VUV and charging effects on the exposed oxide
- Explain how metal redeposition on the wall is created and removed
- Relate trap density at the gate edge to the retention-tail count
- Choose recipe settings that minimize gate-edge damage

---

## 13.1 Which Oxide Is Exposed, and For How Long

### 13.1.1 Exposure Time Versus Depth

The oxide at depth z is uncovered when the recess front passes z and stays exposed for the rest of the main step and for the trim and post-treatment:

```
Front arrival time and remaining exposure, reference array (main step
32.4 s; then trim 6 s and PT 8 s):

  z (nm)    Front passes at    Exposed in ME    + TR + PT
  ─────────────────────────────────────────────────────────
   0          8.7 s             23.7 s           + 14 s
  20         16.2 s             16.2 s           + 14 s
  40         24.1 s              8.3 s           + 14 s
  50         28.2 s              4.2 s           + 14 s
  55         30.3 s              2.1 s           + 14 s
  58         31.6 s              0.9 s           + 14 s
```

The oxide near the silicon surface sees the main step for over 20 s. The oxide just above the gate edge, which matters most for GIDL, sees it for only a few seconds. **For the gate-edge oxide, the trim and post-treatment are a larger share of the exposure than the main step.** Their chemistry (low-energy chlorine, then N₂/H₂) matters as much as the main step's.

### 13.1.2 Where the Field Is

```
Field regions along the wall (schematic, storage-node side):

  z = 0   ┬  n⁺ (highest doping), BC contact above
          │  oxide exposed longest; field low (gate far below)
  z = 40  │
          │  fringing field from the gate edge rises
  z = 55  │  ← high-field band: 5–7 nm above the gate edge
  z = 60  ┼  gate edge (TiN top)
  z = 62  ┼  junction x_j
          │  overlap region: oxide never exposed (under the conductor)
```

The band of highest GIDL field lies across the gate edge, from a few nanometres above it to the junction below it. The upper half of that band is oxide that the recess uncovered during its last few seconds and then exposed to the trim and post-treatment.

---

## 13.2 Oxide Thinning

### 13.2.1 On the Walls

```
Wall oxide loss (illustrative, per wall):

Mechanism                                 Rate                      Loss at z = 0 / 55 nm
──────────────────────────────────────────────────────────────────────────────────────────
Grazing ions, F-assisted                  ≈ 0.5 nm/min equivalent   0.20 / 0.02 nm
Spontaneous F etch of SiO₂ at 50 °C       ≈ 0.05 nm/min             0.02 / < 0.01 nm
Trim (Cl₂, ≤ 20 V)                        ≈ 0.02 nm/min             < 0.01 nm
Total                                                               ≈ 0.22 / ≈ 0.03 nm
```

The walls lose a few tenths of a nanometre at the top and almost nothing near the gate edge, within the specification of ≤ 0.5 nm.

### 13.2.2 At the Shoulder

The 1.4 nm shoulder where the slot narrows at the silicon surface (Chapter 2.1.3) is a horizontal ledge of gate oxide. Once the front passes it, at about 8.7 s, it receives ions at normal incidence for the rest of the etch:

```
Ledge exposure: 23.7 s of ME; oxide rate at normal incidence inside the
slot ≈ 4 nm/min × 0.8 (flux reduced by ARDE) ≈ 3.2 nm/min

  Loss ≈ 23.7/60 × 3.2 ≈ 1.3 nm (from the 3.5 nm oxide at the AA top
  corner)
```

The top corner of the AA is the place where the gate oxide is thinnest after the recess. It lies at the silicon surface, far from the gate edge, so it matters little for GIDL. It matters for isolation between the cap and the AA corner, and it is the place where a pinhole would let fluorine reach the silicon (Chapter 4.6.3). The shoulder loss is one reason the BT energy is limited and the main-step bias is kept near 60 V.

---

## 13.3 Halogens and Hydrogen in the Oxide

### 13.3.1 Fluorine

```
F incorporation in the exposed oxide (illustrative):
  Areal dose in the top 1–2 nm: 10¹³–10¹⁴ cm⁻²
  Later thermal steps (cap deposition at 400–550 °C, junction anneals):
    F diffuses toward the Si/SiO₂ interface
```

Fluorine has two effects at the interface. A small amount replaces Si–H bonds with stronger Si–F bonds and reduces interface traps, which lowers leakage and improves stability. A larger amount creates fixed charge, weakens the oxide network, and lowers its breakdown strength. The recess adds fluorine on top of what the tungsten fill already left (Chapter 2.3.4). The total is what matters.

### 13.3.2 Chlorine

Chlorine from the main step and the trim adsorbs on the oxide and is incorporated less than fluorine. Residual chlorine reacting with moisture in queue forms HCl at the surface, which can attack the nitride-cap nucleation. The post-treatment and a queue-time limit keep it low.

### 13.3.3 Hydrogen

The N₂/H₂ post-treatment exposes the gate-edge oxide to atomic hydrogen. Hydrogen passivates dangling bonds at the interface, but it can also be released later by hot carriers or high fields. That creates interface traps during operation. The post-treatment uses no bias and a short time to limit hydrogen uptake. Some flows use pure N₂ instead.

---

## 13.4 Photons and Charging

### 13.4.1 Vacuum-Ultraviolet Light

The plasma emits vacuum-ultraviolet (VUV) light, especially from argon (104.8 and 106.7 nm) and from fluorine and chlorine atoms and ions. Photons above the SiO₂ band gap (about 9 eV, wavelengths below about 138 nm) are absorbed in the first few nanometres of oxide and create electron–hole pairs. Holes are trapped in the oxide and at the interface, and interface states are created.

```
Illustrative VUV photon flux at the wafer: 10¹⁴–10¹⁵ cm⁻² s⁻¹ (>9 eV)
Dose over the exposure of the gate-edge oxide (≈ 16 s): ≈ 10¹⁶ cm⁻²

Inside the slot, the oxide wall sees photons only within a narrow cone
of solid angle that shrinks with depth:
  Solid-angle fraction at depth d below the slot top ≈ w / (π d)
  At d = 80 nm, w = 11 nm: ≈ 0.04
  → effective dose on the gate-edge oxide ≈ 4×10¹⁴ cm⁻²
```

The slot shields the gate-edge oxide from most of the VUV light. The oxide near the top of the slot, and the shoulder, see far more. That geometry is fortunate. The light reaches mostly the oxide that matters least for GIDL. Argon dilution increases VUV. Replacing argon with helium does not remove it. Helium's resonance line at 58.4 nm (21 eV) is absorbed even closer to the oxide surface.

### 13.4.2 Charging

The antenna ratio of the buried word line is about 0.05 (Chapter 3.6.1), so classic antenna damage is not expected. Electron shading inside the slot is a local effect. During the on-phase, the upper walls charge negative and the bottom charges positive:

```
Illustrative transient wall potential difference: 1–3 V
Across 3.5 nm of oxide (wall to silicon): 3–8 MV/cm during the on-phase,
relaxing in the off-phase of pulsing
```

Such fields drive little current through 3.5 nm of good oxide, but they help separate VUV-generated electron–hole pairs and move holes toward the interface, where they are trapped. Synchronized pulsing, which lets electrons into the slot during the off-phase, reduces both the field and the trapping.

---

## 13.5 Metal on the Wall

### 13.5.1 How It Gets There

The etch products leave the bottom of the slot and strike its walls many times on the way out (Chapter 3.2.3). WF₆ does not stick at 50 °C, but lower fluorides, oxyfluorides, and titanium species can. Ions also sputter a little metal from the bottom onto the walls. In a fluorine-rich gas, tungsten on the wall is fluorinated and leaves again as WF₆. Titanium on the wall forms TiFₓ, which stays.

```
Fate of metal on the wall above the recess (illustrative):

Metal   Arrives as              In ME (F-rich)          In TR (Cl)              After clean
──────────────────────────────────────────────────────────────────────────────────────────────
W       WFₓ, WOₓFᵧ, sputtered   Re-etched to WF₆;       Slowly etched           < 10¹⁰ cm⁻²
                                steady state low
Ti      TiFₓ, sputtered         Accumulates as TiFₓ     Removed as TiCl₄        < 10¹⁰ cm⁻²
                                (involatile)            (BCl₃ not needed: thin)
```

The trim is therefore also a wall-cleaning step for titanium. A recipe that drops the trim to save time leaves titanium fluoride on the gate-edge oxide. The post-recess clean (Chapter 16) removes what remains.

### 13.5.2 Effect

Isolated metal atoms on the oxide surface create states in the oxide band gap near the gate edge. They act as stepping stones for trap-assisted tunnelling. A continuous film, if one formed, would extend the gate electrically up the wall and act like a horn (Chapter 11.2.3).

---

## 13.6 From Damage to Retention

### 13.6.1 GIDL and Trap-Assisted Tunnelling

```
GIDL components at the gate edge:

Band-to-band tunnelling (BTBT)      Needs a high field (> ≈ 1 MV/cm in Si);
                                    strong field dependence; weak T dependence;
                                    set by overlap and doping (Ch. 1.4.1, 10.4)
Trap-assisted tunnelling (TAT)      Uses a trap in the gap as a stepping stone;
                                    works at lower fields; stronger T dependence;
                                    set by trap density and position
```

Damage adds traps, so it raises TAT. TAT is what turns a small number of damaged cells into tail cells, because it depends on whether a trap happens to sit in the high-field band of a particular cell.

### 13.6.2 A Single Trap

```
Leakage from one trap with field-enhanced emission (illustrative):
  Emission rate e ≈ 10⁵ s⁻¹ at the gate-edge field and 95 °C
  I ≈ q × e = 1.6×10⁻¹⁹ × 10⁵ = 1.6×10⁻¹⁴ A = 16 fA

Retention budget (Chapter 1.1.2): 28 fA
```

One well-placed trap can use more than half the cell's leakage budget. Cells with such a trap form the retention tail.

### 13.6.3 Counting Tail Cells

```
High-field area per cell at the gate edge (storage-node side):
  Crossing length over the AA ≈ 14.9 nm × high-field band ≈ 5 nm
  A_edge ≈ 75 nm² = 7.5×10⁻¹³ cm²

Killer-trap density n_k (traps fast enough to exceed ≈ 20 fA; illustrative):
  Baseline:                     1×10⁶ cm⁻²
  Expected per cell:            n_k × A_edge = 7.5×10⁻⁷
  Tail cells per 16 Gb die:     7.5×10⁻⁷ × 1.72×10¹⁰ ≈ 13,000

Recess damage that doubles n_k → ≈ 26,000 tail cells
Overlap +3 nm (horn or shallow recess): larger high-field area and stronger
  enhancement → n_k effectively ×2–3 → 26,000–39,000
```

Tail counts of this order are handled by redundancy and on-die error correction, but every doubling costs repair resources and test time. The overlap (Chapter 10) and the damage (this chapter) multiply each other. A damaged oxide is worse at a shallow recess than at a deep one.

### 13.6.4 Variable Retention Time

Some traps switch between two configurations, so their cell's leakage switches between two values over minutes or hours. Such cells pass a retention test once and fail the next time. This is **variable retention time** (VRT). Traps at the gate edge in damaged oxide, and those associated with hydrogen and with metal on the oxide, are prime suspects. VRT cells cannot be screened by a single test, so they are especially costly. Damage reduction at the gate edge is the main defence.

---

## 13.7 Reliability

```
Reliability concern                   Recess-related cause                   Monitor
──────────────────────────────────────────────────────────────────────────────────────
Gate-oxide TDDB at the gate edge      Thinning, F weakening, horn tip field   TDDB on WL test
(V_PP ≈ 2.9 V across 3.5 nm at                                                structures
low duty: ≈ 8 MV/cm when active)
Hot-carrier degradation of the        H and traps at the gate edge           Stress of cell-
cell transistor                                                               array test keys
Threshold-voltage shift (PBTI-like)   Trapped holes from VUV, F charge        V_T drift after
                                                                              stress
VRT population growth                 Metastable traps (H, metal)            Repeated retention
                                                                              tests
```

The cell oxide runs at a high field when its word line is active. The field is applied only a small fraction of the time, which is why the oxide survives, but it leaves little margin for local weakening at the gate edge.

---

## 13.8 Damage-Aware Recipe Design

```
Choice                                  Effect on gate-edge damage           Cost
──────────────────────────────────────────────────────────────────────────────────────────
Main-step ion energy ≤ 60 eV, narrow    Less wall and shoulder loss;          Lower W rate;
IED (Ch. 6)                             fewer energetic F⁺                    horn risk
Synchronized pulsing                    Less charging and hole trapping      +7 s
Cl-rich main step                       Lower spontaneous F on oxide and Si  TiN–W balance
                                                                             (Ch. 4, 11)
Lower Ar fraction                       Less VUV                             Less sputter of
                                                                             TiFₓ
Keep the trim (Cl₂, low energy)         Removes Ti from the walls             6 s
Bias-free, short PT; N₂ instead of      Less H uptake                         Less halogen
N₂/H₂ where possible                                                         removal
Landing step / quasi-ALE for the last   Lower energy at the gate edge        Time
10–15 nm (Ch. 6.5, 7.4)
Short queue to post-recess clean        Less HF/HCl formation on the oxide   Scheduling
```

---

## 13.9 Summary & Key Takeaways

1. **The gate-edge oxide is exposed briefly, but late.** The oxide just above the gate edge sees only a few seconds of the main step. The trim and post-treatment are most of its exposure.

2. **Thinning is small on the walls and largest at the shoulder.** Walls lose a few tenths of a nanometre at the top and almost nothing near the gate edge. The AA-top shoulder loses about 1.3 nm.

3. **Halogens and hydrogen are mixed blessings.** Some fluorine passivates the interface. More creates charge and weakens the oxide. Hydrogen passivates now and can depassivate later.

4. **The slot shields the gate edge from VUV.** The solid angle at 80 nm depth is about 4%, so the oxide near the top gets most of the light.

5. **Titanium stays on the wall unless chlorine removes it.** Tungsten on the wall is re-etched by fluorine. TiFₓ needs the trim's chlorine.

6. **One trap can make a tail cell.** A field-enhanced trap emitting 10⁵ s⁻¹ leaks 16 fA. Tail counts scale with killer-trap density times the high-field area, and both damage and overlap multiply them.

---

## Study Questions

1. Using the exposure-time table, compute the total exposure of the oxide at z = 45 nm, weighting the main step at 1.0, the trim at 0.2, and the PT at 0.1 for damage. What fraction of the weighted exposure comes from the trim and PT?

2. A recipe raises the main-step bias so that the in-slot normal-incidence oxide rate becomes 6 nm/min. Compute the shoulder loss. If the minimum oxide allowed at the AA corner is 2.0 nm, is the recipe acceptable?

3. Compute the VUV solid-angle fraction at depths of 10, 30, and 80 nm below the slot top for w = 11 nm. If the open-surface dose is 1.5×10¹⁶ cm⁻², what dose does the oxide at each depth receive?

4. A damage experiment shows that the killer-trap density rises from 1×10⁶ to 3×10⁶ cm⁻² when the trim is removed. Compute the tail cells per 16 Gb die before and after. If redundancy and ECC can handle 30,000 tail cells per die, is removing the trim acceptable?

5. Explain why the same oxide damage costs more retention yield at z_r = 56 nm than at z_r = 62 nm. Use the BTBT and TAT mechanisms in your answer.

---

**Next Chapter:** [Chapter 14: Advanced Schemes — Dual-Work-Function Gates, New Metals, ALE, 4F² & 3D DRAM](./14-advanced-wordline-schemes.md)

---

**Chapter 13 Development Status:** Complete  
**Version:** 1.0
