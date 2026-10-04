# Chapter 16: Post-Recess Integration, Yield & Cost of Ownership

## Overview

When the wafer leaves the recess chamber, the conductor top is at its final depth, but the word line is not finished. It still has to survive a clean that must not dissolve tungsten or TiN, a queue during which its surface oxidizes, a nitride cap that must fill the slot above it without voids, a cap polish, and two self-aligned contact etches that land beside it, relying on the cap. Each of these steps uses the recessed surface, and each turns a particular recess defect into a particular yield loss. At the end, the recess is judged by bitmaps and parametric tests, and its cost is weighed against what it saves.

This chapter covers the post-recess clean and queue time, the nitride cap and its fill, the contact modules that rely on the cap, the defect modes and their yield signatures, and the throughput, consumables, and cost of ownership of the recess module.

**Learning Objectives:**
- Choose a post-recess clean that removes residue without etching W, TiN, or the gate oxide
- Set a queue-time limit from tungsten oxidation and halogen residue
- Explain how the nitride cap fills the recessed slot and where it fails
- Trace how recess defects become contact shorts and other yield losses
- Read bitmap and parametric signatures back to their recess causes
- Build a cost-of-ownership estimate and compare it with the value of yield

---

## 16.1 Post-Recess Clean

### 16.1.1 What the Clean Must Do

```
Remove:     W and Ti oxyhalide residue; adsorbed F and Cl; S; Ti on the
            oxide walls; particles
Must not:   etch W (> 0.3 nm), TiN (> 0.3 nm), or the gate oxide (> 0.2 nm);
            leave water in the slot; corrode the metal top
```

### 16.1.2 Chemistry Choices

```
Chemistry                       W        TiN      SiO₂     Residue    Notes
                                attack   attack   attack   removal
───────────────────────────────────────────────────────────────────────────────────
Dilute HF                       Low      Low      High     Good       Thins the gate
                                                                      oxide: avoided
SC-1 (NH₄OH/H₂O₂)               High     High     Low      Good       Dissolves W as
                                                                      tungstate: avoided
Dilute acid, low oxidizer       Low      Low      ≈ 0      Moderate   Common choice
(e.g. dilute organic or
mineral acid)
Solvent-based residue remover   ≈ 0      ≈ 0      ≈ 0      Good for   Cost, waste
                                                           organics
DI water + megasonic, IPA dry   ≈ 0      ≈ 0      ≈ 0      Weak       Rinse only
```

Tungsten dissolves in alkaline oxidizing solutions as tungstate, and TiN dissolves in peroxide. The cleans that work for most front-end surfaces are therefore excluded. The reference flow uses a short, dilute, low-oxidizer acidic clean followed by an IPA dry, and relies on the in-situ post-treatment (Chapter 4.8.2) to have already removed most of the halogen.

### 16.1.3 Queue Time

```
Tungsten top after the recess (illustrative):
  With N₂/H₂ PT, in cleanroom air: WOₓ ≈ 0.5 nm at 4 h, ≈ 1.0 nm at 24 h
  Without PT: WOₓFᵧ grows faster (residual F + moisture → HF on the
  surface), ≈ 1.5 nm at 4 h, with haze

Effects of a thicker WOₓ under the cap:
  Higher contact resistance at the WL pads; WOₓ is partly volatile and
  outgasses during cap deposition; weak cap adhesion
```

The reference limits are recess → clean ≤ 2 h and clean → cap ≤ 4 h.

---

## 16.2 The Nitride Cap

### 16.2.1 Fill

```
Slot to fill: 11 nm wide (13.8 nm in the mask), 88 nm deep from the mask
top → A ≈ 8

Cap sequence (illustrative):
  1. In-situ NH₃ or N₂ plasma: reduce WOₓ, nitride the W top
  2. ALD SiN liner, 1.5–2 nm (fills TiN slits ≤ 3 nm deep, Ch. 11.3.3)
  3. CVD or ALD SiN bulk fill, to close the slot
  4. Anneal (densification), 450–550 °C
```

A conformal fill of an 11 nm slot leaves a seam down the centre of the cap, just as the tungsten fill did. The cap seam is harmless as long as no later wet step opens it. An HF-containing clean before the contact etch, or the contact etch's own clean, can widen it.

### 16.2.2 How the Recess Shape Affects the Cap

```
Recess surface                Cap outcome                        Later risk
──────────────────────────────────────────────────────────────────────────────────
Flat, Δ_TW ≈ 0                Uniform liner, seam at centre       Low
Horn (+3 nm)                  Liner wraps the horn; cap thinner   BC etch reaches the
                              at the wall                         horn if misaligned
Slit (−3 nm, straight)        Filled by ALD liner                 Low
Slit (re-entrant)             Keyhole void along the wall         WL–BC short
V-notch (≤ 2 nm wide)         Filled by liner                     Low
Punch-through cavity          Void at the cap bottom (centre)     Moisture trap;
                                                                  WL open if large
Residue on walls              Poor liner nucleation; weak         Cap delamination;
                              interface                           leakage
```

### 16.2.3 Cap CMP

The cap nitride is polished, and the hard mask is removed or polished back. The remaining cap thickness above the conductor is set by the recess depth and the final polish plane:

```
Reference: polish plane ≈ 20 nm above Si → cap ≈ 80 nm over the W top
(z_r = 60) and ≈ 77 nm over a 3 nm horn
```

A recess that is 5 nm shallow leaves 5 nm less cap, which matters for the self-aligned contact etches (Section 16.3).

---

## 16.3 The Contact Modules

### 16.3.1 Self-Aligned Contacts

The bit-line contact (DC) and the storage-node contact (BC) land on the AA silicon between word lines. Both are etched in a self-aligned contact (SAC) mode: the etch removes oxide quickly and the nitride cap slowly, so a contact that is misaligned toward a word line is stopped by the cap shoulder instead of reaching the word line.

```
SAC margin at the cap shoulder (illustrative):
  Cap nitride loss at the shoulder during the BC etch: 15–25 nm
  Cap height above the W top:                           80 nm
  Margin to the metal:                                  ≈ 55 nm at the centre;
                                                        less at the wall where
                                                        the shoulder is eroded
  Horn of 3 nm at the wall:                             −3 nm of margin exactly
                                                        where the shoulder
                                                        erodes fastest
```

### 16.3.2 Word-Line Contacts at the SWD Pads

The word-line contact is etched through the cap to land on the pad. If the pad is recessed to 72 nm (Chapter 10.3), the contact must etch through about 92 nm of cap (from a polish plane 20 nm above Si). The contact etch is designed for the deepest pad, with overetch onto metal. Pads recessed beyond the limit risk landing on a thinned conductor.

---

## 16.4 Defect Modes and Yield Signatures

### 16.4.1 From Recess Defect to Failure

```
Recess defect               Mechanism                          Electrical failure
──────────────────────────────────────────────────────────────────────────────────────
Shallow recess (z_r < 55)   Gate–junction overlap high         Retention tail ↑, VRT ↑
Deep recess (z_r > 65)      Underlap                           tWR fails; weak "1"
TiN horn                    High gate edge at the wall; tip    Retention tail; SAC
                            field; less SAC margin             margin loss
TiN veil (failed trim)      Gate edge at the Si surface        Massive GIDL; row fails
TiN slit → cap void         Void opened by BC etch/clean       WL–BC short
Particle stub               Unrecessed metal under a particle  WL–BC or WL–DC short
V-notch / punch-through     Conductor thinned; cap void        R_WL ↑; rarely WL open
Pad over-recess             Thin metal under WL contact        WL contact R ↑; open
Oxide damage at gate edge   Traps in the high-field band       Retention tail, VRT
Metal (Ti) on the wall      TAT stepping stones                Retention tail
```

### 16.4.2 Bitmap Signatures

```
Bitmap pattern                                   Likely recess cause
──────────────────────────────────────────────────────────────────────────────────
Whole sub-word line failing (row stripe,         WL–BC or WL–DC short (stub, slit
  one sub-array)                                 void); WL open; pad contact
Row-parity retention pattern (odd vs. even       SADP slot-width alternation →
  word lines differ)                             depth walk (Ch. 10.2.1)
Retention-tail density higher at the wafer       Edge horns (tilt, temperature),
  edge ring                                      edge deeper/shallower
Rows at the array boundary weaker                Array-edge depth offset; dummy
                                                 WL design (Ch. 10.2.2)
Cells near SWD side of each sub-array weaker     Word-line end widening; pad recess
Random single bits, retention-only, VRT          Gate-edge damage; Ti on walls;
                                                 overlap at the top of the window
Lot-to-lot tail shift with no depth change       TiN composition → horn change;
                                                 trim degradation
```

### 16.4.3 Yield Levers

```
Lever                                          Typical gain (illustrative)
──────────────────────────────────────────────────────────────────────────────
Feed-forward of post-CMP height                Depth 3σ 3.3 → 2.6 nm; tail and
                                               tWR losses ↓
Robust trim + STEM audit                       Horn-related retention loss ↓
Pre-trim horn target with margin (no slits)    WL–BC shorts ↓
Particle control (WAC with BCl₃; plasma-on     Stub shorts ↓
  transitions)
Target slightly deep of centre (≈ 60.5 nm)     Retention fails ↓ at small write cost
DWF gate (at the cost of a second recess)      Window 10 → 18 nm
```

---

## 16.5 Throughput and Cost of Ownership

### 16.5.1 Throughput

From Chapter 5.7, the reference cycle is 120 s, giving 30 wafers/hour per chamber. A six-chamber platform with 85% availability and 90% utilization delivers:

```
6 × 30 × 0.85 × 0.90 × 8760 h ≈ 1.2 million wafers per year
```

### 16.5.2 Cost per Wafer

```
Cost element (illustrative)                         Basis                         $/wafer
────────────────────────────────────────────────────────────────────────────────────────────
Depreciation                                        $30M platform (6 chambers),   4.97
                                                    5 years, 1.2M wafers/yr
Edge rings                                          $2k per ring, ≈ 800 RF h;      0.05
                                                    ≈ 71 s RF per wafer
Wet-clean parts (liner, window refurbish)           $15k per ≈ 2500 RF h           0.12
ESC replacement                                     $150k per chamber per          0.25
                                                    ≈ 3 years
Gases (SF₆, Cl₂, NF₃, BCl₃, Ar, N₂, H₂, O₂)          Recipe + WAC                    0.50
Power, cooling, exhaust abatement                                                   0.30
Maintenance labor and downtime                                                      0.80
Metrology (OCD, XRF, STEM audit, e-beam share)                                      1.00
Facilities (floor space, utilities)                                                 1.00
────────────────────────────────────────────────────────────────────────────────────────────
Total                                                                         ≈ $9.0/wafer

DWF word line (two recesses):                                                ≈ $18/wafer
```

### 16.5.3 The Value of Yield

```
16 Gb die ≈ 54 mm² → ≈ 1150 good-candidate dies per 300 mm wafer
Illustrative die value $3.50 → wafer value ≈ $4,000

Value of 0.1% yield:  0.001 × $4,000 = $4.00 per wafer
Recess module cost:   $9.00 per wafer ≈ 0.23% yield
```

A change that improves yield by 0.25% pays for the whole recess module. Feed-forward APC, the trim, and the per-wafer WAC each cost far less than their yield benefit. The question for a new option is rarely whether it costs money. It is whether it costs throughput. The DWF gate doubles the module cost, about $9 per wafer or about 0.2% yield. It is worth it once the single-recess window can no longer contain the depth budget.

### 16.5.4 Where the Cost Is Hidden

```
Hidden cost                                         Why it matters
──────────────────────────────────────────────────────────────────────────────
Repair resources used by retention tail cells       Fewer spare rows/columns for
                                                    other defects
Test time for VRT screening                         Repeated retention tests
Field returns from marginal cells                   Retention and row-hammer
                                                    sensitivity in the field
Chamber count for two recesses                      Floor space and capital for DWF
```

---

## 16.6 Summary & Key Takeaways

1. **The clean must spare the metals.** SC-1 dissolves tungsten and TiN, and HF thins the gate oxide. A dilute, low-oxidizer acidic clean plus the in-situ post-treatment is the usual answer. Queue times of a few hours keep the W oxide thin.

2. **The cap inherits the recess shape.** A flat top fills cleanly. Horns thin the cap at the wall, re-entrant slits leave keyhole voids, and punch-throughs leave centre voids.

3. **Self-aligned contacts depend on the cap.** The BC and DC etches use the cap shoulder as their stop. A horn removes margin where the shoulder erodes fastest, and a void becomes a short.

4. **Each recess defect has a signature.** Row stripes point to shorts or opens, row-parity patterns to depth walk, edge rings to edge horns, and random VRT bits to gate-edge damage.

5. **The module costs about $9 per wafer, about 0.23% yield.** Control measures pay for themselves many times over. Throughput, not cost, is the usual limit on new options.

6. **The DWF gate doubles the cost to widen the window.** It is worth it when the depth budget no longer fits inside a single-recess window.

---

## Study Questions

1. A clean removes residue in 60 s and etches W at 0.004 nm/s, TiN at 0.003 nm/s, and SiO₂ at 0.001 nm/s. Is it within the limits of Section 16.1.1? What is the maximum time?

2. A lot waits 30 h before the cap because of a tool down. Estimate the WOₓ thickness with and without the post-treatment. What would you check before releasing it to the cap, and what are the risks?

3. The BC etch erodes 22 nm of cap at the shoulder. With an 80 nm cap over the W top, compute the margin at the wall for Δ_TW = 0, +3, and +5 nm, and for a recess 5 nm shallow with Δ_TW = +3 nm. Which case is closest to failure?

4. A bitmap shows a retention-tail density 40% higher in the outer 4 mm of the wafer and no depth difference in OCD. List two recess causes, and the measurement that distinguishes them.

5. A quasi-ALE landing would reduce the depth 3σ from 2.6 to 2.0 nm but lowers throughput from 30 to 24 wafers/hour. Compute the extra cost per wafer (depreciation and facilities scale with chamber count). How much yield gain is needed to break even?

---

**Book #27 Complete.** Continue to the appendices for reference data, procedures, and calculations: [Appendix A](../appendices/A-material-properties.md)

---

**Chapter 16 Development Status:** Complete  
**Version:** 1.0
