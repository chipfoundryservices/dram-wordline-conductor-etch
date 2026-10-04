# Chapter 10: Recess Depth Control & the Gate–Junction Overlap Window

## Overview

Chapter 1 set the target: the conductor top at z_r = 60 nm below the silicon surface, within ±5 nm, so that the gate overlaps the 62 nm storage-node junction by between −3 and +7 nm. This chapter asks whether production can hold that window and what it costs when it does not. It assembles the depth budget from the incoming CMP height, the etch itself, the slot width, and the surface, adds the junction variation that the overlap also depends on, and maps depth errors onto GIDL, write current, row hammer, and word-line resistance. It then looks at the places in the die where depth is hardest to control: the array edge, alternating word lines from multiple patterning, and the wide pads at the sub-word-line drivers.

**Learning Objectives:**
- Build a recess-depth budget and an overlap budget from their contributors
- Show the value of feed-forward from the post-CMP height
- Predict depth variation across the array edge and between alternating word lines
- Evaluate the SWD pad depth against its limit and choose design and process levers
- Map recess depth onto GIDL, retention tail, write failures, row hammer, and word-line resistance
- Choose a target inside the window when the costs on each side differ

---

## 10.1 The Depth Budget

### 10.1.1 Contributors

```
Contributor (3σ, illustrative)                  Raw        After feed-forward
───────────────────────────────────────────────────────────────────────────────
Incoming starting height (CMP erosion,          ±2.3 nm    ±1.0 nm
  dishing, mask thickness) (Ch. 2.4.4)
Recess etch, within wafer (radial, after        ±1.5 nm    ±1.5 nm
  tuning) (Ch. 7, 8)
Recess etch, wafer to wafer (wall state,        ±1.0 nm    ±1.0 nm
  drift) (Ch. 9)
Chamber to chamber, residual after APC          ±0.7 nm    ±0.7 nm
  constants (Ch. 5.7)
Slot width via ARDE (±1.2 nm CD × 0.87)         ±1.05 nm   ±1.05 nm
  (Ch. 3.3.4)
Local top-surface variation (seam, grains)      ±0.8 nm    ±0.8 nm
  (Ch. 12)
Breakthrough start (skin thickness)             ±0.5 nm    ±0.5 nm
  (Ch. 4.7)
───────────────────────────────────────────────────────────────────────────────
RSS, z_r                                        ±3.3 nm    ±2.6 nm
```

Without feed-forward, the CMP starting height is the largest term. With feed-forward of the measured post-CMP height into the etch time (Chapter 15), it falls below the etch's own within-wafer term. The remaining terms are spread fairly evenly. No single fix halves the budget.

### 10.1.2 The Overlap Budget

The device sees the overlap, Δ_ov = x_j − z_r, not z_r alone. The junction depth varies too:

```
Junction depth x_j (implant energy, dose, anneal, and the silicon
consumed by later oxidations): ±2.0 nm (3σ, illustrative)

Overlap budget:
  Raw:          √(3.3² + 2.0²) = ±3.9 nm
  Feed-forward: √(2.6² + 2.0²) = ±3.3 nm

Window: Δ_ov from −3 to +7 nm, centred at +2 → ±5 nm available
  Margin raw:          5 − 3.9 = 1.1 nm
  Margin feed-forward: 5 − 3.3 = 1.7 nm
```

The window holds, but the margin is about 1–2 nm. At the next node, where the window shrinks to about ±4 nm (Chapter 1.5.3), it does not hold without further reduction. The levers are a tighter CMP, a smaller k (pulsing, landing steps), a tighter word-line CD, and a dual-work-function gate that widens the GIDL side of the window (Chapter 14).

---

## 10.2 Depth Across the Array

### 10.2.1 Alternating Word Lines

Word lines at 34 nm pitch are patterned by self-aligned double or quadruple patterning. As in the active-area patterning of Book #26, the spacer process leaves trench widths that alternate. With self-aligned double patterning (SADP), odd and even word lines differ:

```
SADP word lines (illustrative):
  Core-defined trenches:    18.0 + 0.4 nm
  Gap-defined trenches:     18.0 − 0.4 nm
  Slot widths:              11.4 and 10.6 nm

Depth walk (∂z_r/∂w = 0.87):  ±0.35 nm  → odd/even difference ≈ 0.7 nm
```

A 0.7 nm odd/even difference is small against the window, but it is systematic. Every cell on an odd word line has a slightly different gate edge from its neighbor on an even word line. It shows in retention bitmaps as a row-parity pattern when the window is tight.

### 10.2.2 The Array Edge

At the array edge, three effects meet: the SAQP or SADP lines end and the outermost trenches are wider or narrower, the CMP erosion falls from the array value to the field value over a few micrometres, and the pattern density for the plasma changes. Dummy word lines absorb most of this, but not all:

```
z_r by word-line position from the array edge (illustrative):

Position          Slot w_s   Mask top   h₀ (nm)   z_r (nm)   Driver
                  (nm)       (nm)                            ──────────────
Dummy 1           12.5       29.5       2         58.9       Wider, higher start
Dummy 2           11.2       29.0       2.5       58.8
WL 1 (first real) 11.0       28.8       2.8       59.0       Higher start
WL 2              11.0       28.4       2.9       59.5
WL 3              11.0       28.2       3.0       59.8
WL ≥ 5            11.0       28.0       3.0       60.0       Array value
```

The first real word lines start a little higher because the CMP erodes the mask less near the boundary, so they finish a little shallower. With two dummy word lines, the first real word line is within about 1 nm of the array, and the third is within 0.2 nm. Without dummies, the first word line would be the wide outermost trench and would end about 1.5 nm deeper or shallower, depending on which effect dominates.

### 10.2.3 Word-Line Ends Inside the Array

Where word lines end at the edge of a sub-array and turn into a strap or connect to a driver, the end region is wider and recesses deeper (Chapter 3.4.2). The cells nearest a word-line end are the most likely to see a different gate edge. Layout keeps the last real cell a fixed distance from the widening.

---

## 10.3 The Sub-Word-Line Driver Pads

### 10.3.1 The Problem

```
Reference pad: 40 nm wide, dished 8 nm in CMP
  z_r(pad) = 71.9 nm (Chapter 3.4.1)
  Limit:     ≤ 75 nm
  Margin:    3.1 nm (but pads are not in the feed-forward measurement)
```

A pad that recesses too far leaves a thin conductor under the word-line contact and makes the contact etch go deeper through the cap. If the pad recess approaches the conductor bottom in a shallow end region, the contact can land on the gate oxide instead of the metal.

### 10.3.2 Levers

```
Lever                                   Pad z_r change     Side effects
──────────────────────────────────────────────────────────────────────────────
Narrower pad (40 → 30 nm)               −1.3 nm            Smaller contact landing
Reduce pad dishing (CMP dummy fill,     −2 to −3 nm        Layout area; CMP recipe
  slurry selectivity) 8 → 5 nm
Lower k (pulsed 30% duty; landing        −1.5 to −3 nm      Longer etch (Ch. 6, 7)
  step)
Pad-local protection (block mask)       Pad held at        Extra litho step; rarely
                                        any depth          justified
Contact etch tuned for deeper pad       0 (accepts depth)  Longer contact etch, more
                                                           cap loss elsewhere
```

The usual combination is a narrower pad and reduced dishing, which together bring the pad to about 67–69 nm and give the contact etch a comfortable target.

---

## 10.4 What Depth Does to the Device

### 10.4.1 Overlap, GIDL, and Drive

Using the illustrative model of Chapter 1.4.1 (GIDL one decade per 8 nm of overlap; I_on −4% per nm of underlap):

```
z_r (nm)   Δ_ov (nm)   GIDL (rel.)   I_on (rel.)   R_SWL (rel.)
────────────────────────────────────────────────────────────────
53          +9           7.5           1.00          0.94
55          +7           4.2           1.00          0.95
57          +5           2.4           1.00          0.97
60          +2           1.0           1.00          1.00
63          −1           0.42          0.96          1.03
65          −3           0.24          0.88          1.05
67          −5           0.13          0.80          1.07
```

### 10.4.2 Retention and Write Failures

The device effects become yield through two failure counts. Retention failures come from cells whose total leakage exceeds the budget at the refresh interval. GIDL is one component, along with junction leakage, trap-assisted tunnelling, and subthreshold leakage. Write failures (tWR) come from cells whose drive is too weak to restore a full level in the write time.

```
Illustrative fail-bit counts relative to the target (z_r = 60 nm):

z_r (nm)   Retention fails      Write (tWR) fails
           (64 ms, 95 °C)       (min. tWR, low V)
──────────────────────────────────────────────────
53          6.5×                 1.0×
55          3.4×                 1.0×
57          2.0×                 1.0×
60          1.0×                 1.0×
63          0.8×                 1.5×
65          0.75×                4×
67          0.75×                20×
```

Retention fails flatten below the target, because other mechanisms (isolation sidewall, junction, capacitor) take over once GIDL is small. Write fails stay flat above the target until underlap begins and then rise steeply. The two curves are asymmetric. Over-recess costs little until about 63 nm and then a great deal. Under-recess costs steadily from the start.

### 10.4.3 Row Hammer

Deeper recess also lowers the coupling from passing word lines to their neighbors' storage-node junctions:

```
Illustrative row-hammer threshold (activations before the first bit flip,
relative to target):

z_r (nm)            55      57      60      63      65
Threshold (rel.)    0.80    0.90    1.00    1.12    1.25
```

The trend favors a deeper recess, with the same asymmetry. Write margin limits how far the target can move.

### 10.4.4 Word-Line Resistance

```
R_SWL ≈ 13.9 kΩ × (108 / (108 − (z_r − 60)))

z_r = 65 nm: 13.9 × 108/103 = 14.6 kΩ   (+4.9%)
Limit 15.0 kΩ → z_r ≤ 67.9 nm
```

Resistance is not the binding constraint in the reference process. It becomes binding in narrower slots with thinner tungsten cores, where the W fraction of the conductor falls (Chapter 14).

---

## 10.5 Choosing the Target

### 10.5.1 The Asymmetric Window

With the fail-count curves above, the yield-optimal target is not the centre of the overlap window. A small move toward deeper recess lowers retention fails and raises the row-hammer threshold, while write fails stay flat until underlap begins:

```
Expected relative fail cost for a Gaussian z_r distribution with σ = 0.87 nm
(the feed-forward 3σ = 2.6 nm), weighting retention and write fails equally
(illustrative):

Target z_r (nm)    Relative cost
──────────────────────────────────
59                 1.10
60                 1.00
61                 0.99
62                 1.05
63                 1.26
```

The minimum lies between 60 and 61 nm, about half a nanometre deeper than the centre of the window. The cost curve is flat on the deep side and steep on both ends. A target error of 1 nm toward shallow costs about 10%, and 2 nm toward deep costs about 5%. The best target depends on the product. A server part with long refresh intervals favors deeper recess. A high-speed graphics or HBM part with tight write timing favors staying at or above the centre.

### 10.5.2 Target and Junction Together

The target is meaningful only together with the junction. If the implant or anneal moves x_j, the recess target must move with it to keep the overlap. In practice the recess target is set at integration and changed only with a matched junction change, and the APC holds z_r, not Δ_ov, because z_r is what can be measured at the recess step.

---

## 10.6 Summary & Key Takeaways

1. **The depth budget is about ±3.3 nm raw and ±2.6 nm with feed-forward.** The CMP starting height is the largest raw term, and feed-forward removes most of it.

2. **The overlap budget includes the junction.** With x_j at ±2 nm, the overlap varies by about ±3.3–3.9 nm in a ±5 nm window. The margin is 1–2 nm at the reference node.

3. **Multiple patterning makes alternating depths.** A ±0.4 nm SADP width difference gives about a 0.7 nm odd/even depth difference, which can appear as a row-parity pattern.

4. **Array edges and pads need design help.** Dummy word lines bring the first real word line within about 1 nm. Pads end about 12 nm deeper and are brought back with narrower pads and less dishing.

5. **The device costs are asymmetric.** Under-recess raises retention fails steadily. Over-recess is nearly free until underlap, then write fails rise steeply. Row hammer favors deeper recess.

6. **The best target is slightly deep of centre.** For equal weighting, the optimum is about 60.5 nm, and the cost rises faster on the shallow side. The target must move with the junction.

---

## Study Questions

1. Feed-forward reduces the CMP term to ±1.0 nm. Which single further improvement (radial etch to ±1.0 nm, CD to ±0.8 nm, or k to 0.025) reduces the z_r RSS most? Compute each.

2. At the next node the window is Δ_ov from −2.5 to +5.5 nm, x_j varies by ±1.8 nm, and the slot is 9.6 nm with ∂z_r/∂w = 1.0. Using the other feed-forward terms of Section 10.1.1, is the window met? What is the margin or shortfall?

3. An SAQP word-line process leaves three slot widths: 10.4, 11.0, and 11.6 nm. Compute the depth of each and the maximum depth difference. How would this appear in a retention bitmap?

4. Using the fail-count table, compute the expected relative retention and write fail counts for a process centred at 60 nm with σ = 1.1 nm (no feed-forward), by summing over 1 nm bins from 56 to 64 nm. Compare with σ = 0.87 nm.

5. A product moves to a longer refresh interval, which doubles the weight of retention fails. Recompute qualitatively where the optimal target moves, and what limits how far it can go.

---

**Next Chapter:** [Chapter 11: TiN–W Differential Recess — Horns, Pullback & Cap Integrity](./11-tin-w-differential-recess.md)

---

**Chapter 10 Development Status:** Complete  
**Version:** 1.0
