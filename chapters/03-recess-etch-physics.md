# Chapter 3: Metal Recess Physics in Narrow Slots

## Overview

A blanket metal etchback on an open surface is simple: the rate is set by the radical and ion fluxes, and depth is rate times time. The word-line recess differs in one way that drives most of its behavior. **It digs its own slot.** At the start, the metal surface is nearly level with the hard mask. At the end, it lies 88 nm down a hole 11 nm wide. The radicals that etch the tungsten must reach the bottom of that hole by bouncing off its oxide walls. The ions must arrive at angles steep enough not to hit the walls first. The etch products must find their way out. The rate falls as the hole deepens, and how fast it falls depends on the slot width.

This chapter builds the physics of the recess from the surface reaction up: ion-enhanced metal etching and the fluxes it needs, free-molecular transport in a deepening slot, the ARDE time-to-depth curve and its width sensitivity, ion shadowing at the slot corners, charging, and loading by the exposed metal across the wafer.

**Learning Objectives:**
- Estimate radical and ion fluxes and the fraction of each used in tungsten recess
- Apply the Coburn–Winters model and the linear ARDE form to a slot of rising aspect ratio
- Compute recess time to depth and the depth sensitivity to slot width
- Predict the recess of wide features (pads, ends) relative to the array
- Estimate ion shadowing at the slot corners and its effect on TiN
- Explain why antenna charging is weak for buried word lines and what replaces it
- Estimate global loading from the exposed metal fraction

---

## 3.1 Ion-Enhanced Metal Etching

### 3.1.1 The Two Paths

Tungsten reacts with fluorine atoms at room temperature without ion help. The product WF₆ boils at 17 °C, so once it forms it leaves the surface. The spontaneous rate, though, is limited by the slow formation of the higher fluorides from the lower ones on the surface, and by any oxide or nitride skin. Ion bombardment speeds this up by breaking surface bonds, mixing fluorine into the top few monolayers, and removing the less volatile lower fluorides and oxyfluorides.

```
Tungsten etch paths:

  Spontaneous:     W(s) + 6F(g) → WF₆(g)           rate ∝ s_F Γ_F
                   (s_F: reaction probability per F atom, ~10⁻² at 50 °C,
                    illustrative)

  Ion-enhanced:    WFₓ(ads) + ion → WF₆↑, WFₓ↑      rate ∝ Y_i Γ_i
                   (Y_i: W atoms removed per ion, several at 50–100 eV
                    with a fluorinated surface)

Series form (one path feeds the other):
  1/ER = 1/(a s_F Γ_F) + 1/(b Y_i Γ_i)
```

TiN behaves differently. TiF₄ does not sublime until about 284 °C, so in fluorine the TiN surface becomes a fluoride crust that ions must sputter. In chlorine, TiCl₄ (boiling point 136 °C) is volatile, and TiN etches with modest ion help. Chapter 4 develops the chemistry.

### 3.1.2 Flux Estimates

```
Reference plasma (illustrative): 8 mTorr, F atom density n_F = 3×10¹³ cm⁻³,
gas temperature 400 K; ion current density J_i = 1.0 mA/cm²

F mean speed:  v̄ = √(8kT/πm) = √(8 × 1.38×10⁻²³ × 400 / (π × 19 × 1.66×10⁻²⁷))
               ≈ 668 m/s
F flux:        Γ_F = n_F v̄ / 4 = 3×10¹⁹ m⁻³ × 668 / 4 = 5.0×10²¹ m⁻² s⁻¹
                   = 5.0×10¹⁷ cm⁻² s⁻¹
Ion flux:      Γ_i = J_i / e = 1.0×10⁻³ / 1.602×10⁻¹⁹ = 6.2×10¹⁵ cm⁻² s⁻¹

Open-area W rate 3.0 nm/s (180 nm/min):
  W atoms removed:  3.0×10⁻⁷ cm/s × 6.31×10²² cm⁻³ = 1.9×10¹⁶ cm⁻² s⁻¹
  F needed:         6 × 1.9×10¹⁶ = 1.14×10¹⁷ cm⁻² s⁻¹  → 23% of Γ_F
  W per ion:        1.9×10¹⁶ / 6.2×10¹⁵ ≈ 3.1
```

The fluorine flux is about four times what the etch needs, and each ion takes about three tungsten atoms with it. The open-area etch is close to the balance point between the two paths. That matters inside the slot, where both fluxes fall but by different amounts.

---

## 3.2 Transport in a Deepening Slot

### 3.2.1 Free-Molecular Flow

At 8 mTorr the mean free path of a neutral is several millimetres, a hundred thousand times the slot width. Inside the slot, radicals move in straight lines between wall collisions. The walls are oxide. A fluorine atom that strikes the oxide wall at 50 °C under low ion bombardment mostly re-emits in a random direction (diffuse reflection) and occasionally recombines. Only at the metal bottom does it react, with probability β.

### 3.2.2 The Coburn–Winters Model

The flux reaching the bottom of a feature, relative to the flux arriving at its top, depends on the feature's transmission probability K and the bottom reaction probability β:

```
Γ_bottom / Γ_top = K / (K + β (1 − K))

K: probability that a molecule entering the top reaches the bottom
   without returning (for a lossless wall)
β: probability that a molecule hitting the bottom reacts
```

A long slot of depth h and width w has aspect ratio A = h/w. Its transmission falls with A. The simple form K ≈ 1/(1 + A/2) captures the trend and leads directly to the linear ARDE form. It underestimates the transmission of a long slot at large A, where molecules travel far along the slot and a logarithmic correction appears (Appendix E.2 gives Monte Carlo values). Even so, the linear ARDE form with a fitted k reproduces measured depth series within a few percent over A = 0–10. Substituting:

```
Γ_bottom / Γ_top = 1 / (1 + β A / 2)

Linear ARDE form:   ER(A) / ER₀ = 1 / (1 + k A)    with  k ≈ β/2
```

For the reference process, depth-series measurements give k = 0.035 for the main recess step. With the simple transmission form this corresponds to β ≈ 0.07. With the long-slot transmission from the Monte Carlo of Appendix E.2, which falls more slowly at large A, the same data give β ≈ 0.1. Either value is plausible for fluorine on a tungsten surface kept active by ions. The fitted k is what the rest of the book uses. The coefficient is a property of the step, not of the slot. Higher bias, pulsing, and chlorine content all change it (Chapters 6 and 7).

### 3.2.3 Etch Products

WF₆ and the other products leave the bottom in random directions and must also escape the slot. Their flux out of the slot equals the etch rate times the metal density times the slot area, so they do not build up in steady state. They do strike the walls many times on the way out. At 50 °C WF₆ does not stick to oxide, but the lower fluorides and oxyfluorides (WOF₄, WF₄) and the titanium species can. A thin redeposit on the slot wall above the metal is the source of the metal-on-oxide contamination of Chapter 13.

---

## 3.3 Time to Depth

### 3.3.1 The Recess Equation

The hole depth h is measured from the top of the hard mask beside the slot. It grows at the ARDE-limited rate:

```
dh/dt = ER₀ / (1 + k h / w)

Integrating from the starting hole depth h₀:
  ER₀ t = (h − h₀) + (k / 2w)(h² − h₀²)
```

### 3.3.2 The Reference Array

In the array, the mask top is at 28 nm above the silicon after 2 nm of CMP erosion. The metal starts 3 nm below it (dishing). The target is z_r = 60 nm, so the final hole depth is 88 nm:

```
Array: h₀ = 3 nm, h_end = 88 nm, w = 11 nm, k = 0.035, ER₀ = 3.0 nm/s

  ER₀ t = (88 − 3) + (0.035 / 22)(88² − 3²)
        = 85 + 0.0015909 × 7735
        = 85 + 12.31 = 97.3 nm (open-area equivalent)

  t = 97.3 / 3.0 = 32.4 s

  Rate at the end:  ER = 3.0 / (1 + 0.035 × 8.0) = 2.34 nm/s
  Average rate:     85 / 32.4 = 2.62 nm/s
```

At the end of the etch the slot rate is 78% of the open-area rate, and **one second of etch time moves z_r by 2.3 nm**. The ±5 nm window is ±2.1 s of plasma time.

The upper 30 nm of the slot lies in the hard mask, where the slot is 13.8 nm wide instead of 11 nm (Chapter 2). That section has a lower aspect ratio, so the real etch is slightly faster than this model predicts. The fitted k absorbs most of the difference, provided it was extracted on the same stack.

### 3.3.3 Depth Versus Time

```
Conductor-top depth z_r = h − 28 (array) vs. main-etch time (illustrative):

  t (s)     Array z_r (nm)    40 nm pad z_r (nm)
  ──────────────────────────────────────────────
   0          −25.0              −21.0
   5          −10.5               −6.2
  10            3.4                8.4
  15           16.8               22.9
  20           29.7               37.1
  25           42.2               51.2
  30           54.3               65.1
  32.4         60.0               71.9
```

The pad is computed in Section 3.4.

### 3.3.4 Slot-Width Sensitivity

At a fixed etch time, a wider slot recesses deeper. Differentiating the recess equation at fixed t:

```
∂h/∂w = [k (h² − h₀²) / (2w²)] / (1 + k h / w)

Reference:  = [0.035 × 7735 / 242] / 1.28 = 1.119 / 1.28 = 0.87 nm per nm

Slot width (nm)    9.8      10.4     11.0     11.6     12.2
z_r (nm)          58.9     59.5     60.0     60.5     61.0
```

The slot width follows the word-line trench CD one-for-one (Chapter 2.1.4). A ±1.2 nm (3σ) trench CD becomes about ±1.05 nm of recess depth. That is a smaller term than the CMP starting height, but it is not correctable by time, because it varies from word line to word line inside one die.

### 3.3.5 Sensitivity to k

```
k        t to z_r = 60 (s)   End rate (nm/s)   ∂z_r/∂w (nm/nm)   40 nm pad z_r
──────────────────────────────────────────────────────────────────────────────
0.020        30.7               2.59              0.55              68.7
0.035        32.4               2.34              0.87              71.9
0.050        34.2               2.14              1.14              74.9
0.070        36.5               1.92              1.43              78.5
```

A smaller k reduces the width sensitivity and the pad offset together. Pulsing, lower pressure, and a chlorine-rich main step all reduce k (Chapters 6 and 7).

---

## 3.4 Wide Features: Pads and Word-Line Ends

### 3.4.1 Sub-Word-Line Driver Pads

The landing pads at the SWD are about 40 nm wide. Their aspect ratio stays low, so they etch close to the open-area rate. They also start lower, because CMP dishes them more (Chapter 2.4.3):

```
Pad: w = 40 nm, mask top at 29 nm above Si (1 nm erosion), metal starts
     8 nm below → h₀ = 8 nm

Same plasma exposure (ER₀ t = 97.3 nm):
  (h − 8) + (0.035/80)(h² − 64) = 97.3
  0.0004375 h² + h − 105.33 = 0  →  h = 100.9 nm

  Pad z_r = 100.9 − 29 = 71.9 nm   (array: 60.0 nm)
```

The pad ends almost 12 nm deeper than the array. Two effects add. Lower ARDE accounts for about 8 nm of the difference: a 40 nm pad with the array's starting height would end at 68.3 nm. The lower starting height accounts for about 3 nm: an 11 nm slot starting at the pad's height would end at 63.0 nm. The pad's 8 nm of dishing is partly offset by its 1 nm of lower erosion. A pad that recesses too deep leaves less metal under the word-line contact, and the contact etch must go deeper through the cap to land on it. Chapter 10 discusses how layout and CMP are used to hold the pad offset inside the limit of 75 nm.

### 3.4.2 Other Features

```
Same exposure (ER₀ t = 97.3 nm), illustrative starting heights:

Feature                        w (nm)   Mask top   h₀ (nm)   z_r (nm)
─────────────────────────────────────────────────────────────────────
Array WL                       11       28         3         60.0
Isolated WL end                11       30         2         57.2
WL strap / end cap             20       29         4         64.6
SWD pad (narrow design)        30       29         8         70.6
SWD pad (reference)            40       29         8         71.9
Open area (test pad)           ≥ 100    30         15        ≈ 57
```

The isolated word-line end recesses *less* than the array, because it sits where the hard mask was not eroded, so its metal starts 2–3 nm higher. Pattern density and width therefore pull in opposite directions in different places. The open test pad recesses less than the 40 nm pad because it starts much lower after heavy dishing, which is why open-area test structures are poor proxies for the array (Chapter 15).

---

## 3.5 Ions in the Slot

### 3.5.1 Ion Angular Spread

Ions cross the sheath nearly vertically. Their angular spread comes from the ratio of their transverse thermal energy at the sheath edge to the energy gained in the sheath, broadened by any collisions:

```
σ_θ ≈ √(kT_i / (2 e V_sh))   (collisionless; T_i at the sheath edge)

Reference main step: kT_i ≈ 0.05 eV, V_sh ≈ 60 V
  σ_θ ≈ √(0.05 / 120) = 0.020 rad ≈ 1.2°
With sheath collisions at 8 mTorr and low bias: effective σ_θ ≈ 2–3°
```

### 3.5.2 Shadowing at the Corners

A point on the metal surface near the wall can be reached only by ions whose path clears the top edge of the slot on that side:

```
Lateral shadow width at depth h for ions tilted by θ:  s = h tan θ

h = 60 nm (mid-recess), θ = 2.5°:  s = 2.6 nm
h = 88 nm (end),        θ = 2.5°:  s = 3.8 nm

The TiN strip is 2 nm wide, against the wall. Ions tilted toward that wall
by more than about arctan(x/h) cannot reach a point x from the wall.
```

At the wall itself, about half the ions (those tilted toward that wall) are blocked. Averaged across the 2 nm TiN strip, the ion flux at mid-recess is roughly 60–70% of the flux at the slot centre, and it falls further as the recess deepens. In a fluorine-rich step, where TiN removal depends on ion sputtering of the fluoride crust, **shadowing slows the TiN relative to the tungsten as the recess deepens**. That makes TiN horns grow with depth (Chapter 11). In a chlorine-rich step, TiN etches mostly spontaneously and is much less sensitive to shadowing.

### 3.5.3 Wall Reflection

Ions that strike the near-vertical oxide wall at grazing incidence can reflect forward, keeping much of their energy, and land at the foot of the wall. At high ion energy this concentrates flux at the corner and digs a small trench at the TiN–oxide boundary (microtrenching). At the low energies used for recess (under about 100 eV), reflection is weaker and more diffuse, and shadowing usually wins. Corner microtrenching is a sign that the bias is too high (Chapter 6).

### 3.5.4 Ions and the Seam

The slot centre receives the full ion flux, and the seam lies on the centreline. Ion-enhanced etching therefore works hardest exactly where the tungsten is least dense. Chapter 12 shows how this, together with fluorine diffusion along the seam, opens a V-notch.

---

## 3.6 Charging

### 3.6.1 The Word Line as an Antenna

During the recess, each word line is a long floating conductor. It is insulated from the silicon by the gate oxide and collects charge only through its exposed top surface. In logic, a floating gate connected to a large exposed conductor (an "antenna") can collect enough current to stress its thin oxide. The buried word line is the opposite case:

```
Antenna ratio = exposed conductor area / gate-oxide area under it

Per unit length of WL:
  Exposed top:   w_s = 11 nm
  Gate oxide:    2 × h_eff + w_s ≈ 2 × 108 + 11 ≈ 227 nm (walls + bottom,
                 to the conductor top; the oxide above z_r is not under the
                 conductor)
  Antenna ratio ≈ 11 / 227 ≈ 0.05
```

An antenna ratio of 0.05 is tiny. The current collected per unit oxide area is twenty times smaller than the plasma current density, and the voltage the word line can float to is limited by the local balance of ion and electron current at its top. **Classic antenna damage is not the main risk for the buried word line.**

### 3.6.2 Local Charging of the Slot

What remains is electron shading. Electrons arrive nearly isotropically and are captured by the upper walls of the slot. Ions reach the bottom. The metal bottom charges slightly positive relative to the slot walls, and the oxide walls near the top charge negative. The field across the wall oxide above the conductor can deflect ions and, if large, stress the oxide that separates the slot from the silicon. Synchronized pulsing, which lets electrons enter the slot during the afterglow, reduces it (Chapter 6). The oxide above the recess and its damage are the subject of Chapter 13.

---

## 3.7 Global Loading by Exposed Metal

### 3.7.1 How Much Metal

```
Exposed metal fraction on the wafer:
  Array fraction of die:          0.55
  Metal fraction of array top:    11 / 34 = 0.32
  Per die:                        0.55 × 0.32 = 0.18
  Die fraction of wafer (scribe,
    edge exclusion):              ≈ 0.90
  Wafer metal fraction f:         ≈ 0.16

  Metal area on a 300 mm wafer:   0.16 × 707 cm² ≈ 113 cm²
```

### 3.7.2 Fluorine Consumption

```
W removal at the average slot rate (2.6 nm/s), W = 64% of the front:
  113 cm² × 2.6×10⁻⁷ cm/s × 6.31×10²² cm⁻³ × 0.64 ≈ 1.2×10¹⁸ W atoms/s
  F consumed:  6 × 1.2×10¹⁸ = 7.1×10¹⁸ F/s

1 sccm = 4.48×10¹⁷ molecules/s
  F consumption ≈ 16 sccm of F atoms
  WF₆ produced ≈ 2.7 sccm

SF₆ feed 40 sccm, ≈ 20% dissociated, ≈ 3 usable F per dissociated SF₆:
  F supply ≈ 40 × 0.2 × 3 ≈ 24 sccm of F atoms
```

The wafer consumes a large fraction of the fluorine the plasma makes. The etch is strongly **loaded**: its rate depends on how much metal is exposed.

### 3.7.3 The Loading Equation

The classical loading model gives the rate as a function of the exposed area fraction:

```
ER(f) = ER(0) / (1 + Φ f)

Φ: loading factor (ratio of consumption on a fully metal wafer to all
   other loss of F in the chamber)

Reference: rate on a nearly metal-free test wafer is 30% higher than on
product → 1 + 0.16 Φ = 1.30 → Φ ≈ 1.9
```

### 3.7.4 Product-to-Product Differences

```
Product A: array efficiency 0.52 → f = 0.150 → ER/ER(0) = 1/(1 + 0.285) = 0.778
Product B: array efficiency 0.58 → f = 0.167 → ER/ER(0) = 1/(1 + 0.317) = 0.759

Rate difference: 2.5% → over 85 nm, ≈ 2.1 nm of recess depth
```

A chamber that runs several products must use a per-product time constant (Chapter 15). The same effect makes the first and last wafers of a lot differ if the chamber walls change the loss term between them (Chapter 9).

### 3.7.5 Radial Loading

Near the wafer edge, there is no metal beyond the wafer, and the fluorine is less depleted. The edge dies recess faster. With an edge ring that consumes no fluorine, the effect reaches about 10–15 mm in from the edge and is corrected with edge gas injection, edge-ring temperature, and chuck zones (Chapters 7–9).

---

## 3.8 Summary & Key Takeaways

1. **Tungsten recess is ion-enhanced fluorine etching near a balance point.** The open-area etch uses about a quarter of the incoming fluorine and removes about three tungsten atoms per ion.

2. **The recess creates its own ARDE.** With k = 0.035, the rate falls to 78% of open-area by the end. The reference array needs 32.4 s, and one second moves z_r by 2.3 nm.

3. **Width becomes depth.** ∂z_r/∂w ≈ 0.87, so a ±1.2 nm trench CD gives about ±1 nm of recess depth that time cannot correct.

4. **Wide features go deeper, high-starting features stay shallower.** The 40 nm pad ends near 72 nm, about 12 nm below the array. Isolated ends start higher and finish about 3 nm shallower.

5. **The corners see fewer ions.** Shadowing reduces the ion flux on the TiN strip to roughly two-thirds of the centre, which makes TiN horns grow with depth in fluorine-rich steps.

6. **Antenna charging is weak, but the etch is strongly loaded.** The antenna ratio is about 0.05, but the wafer consumes much of the fluorine. Product area fraction, wall state, and wafer edge all move the rate.

---

## Study Questions

1. At 6 mTorr the F density is 2×10¹³ cm⁻³ and the ion current density 0.8 mA/cm². Compute Γ_F, Γ_i, and the fraction of Γ_F needed for an open-area W rate of 150 nm/min. How many W atoms are removed per ion?

2. A depth series gives these array hole depths (from the mask top): 31.4 nm at 10 s, 57.7 nm at 20 s, and 82.3 nm at 30 s, with h₀ = 3 nm and w = 11 nm. Fit ER₀ and k, and compare them with the reference values.

3. For k = 0.035 and ER₀ = 3.0 nm/s, compute the time for an array with h₀ = 5 nm and mask top at 27 nm to reach z_r = 60 nm. Compare with the reference and explain the difference.

4. A layout change makes the SWD pads 28 nm wide. Using the method of Section 3.4.1 and h₀ = 7 nm, compute the pad z_r at the reference exposure. How much does narrowing the pads gain?

5. For σ_θ = 2.5°, estimate the fraction of ions reaching the TiN–oxide corner at h = 30, 60, and 88 nm, assuming a Gaussian angular distribution and blocking of ions tilted toward the near wall by more than arctan(1 nm / h). Sketch the trend and explain the effect on the TiN–W step.

6. A new product has an array efficiency of 0.62. Using Φ = 1.9 and the reference product's f = 0.16, compute the rate change and the z_r shift if the recess time is not adjusted.

---

**Next Chapter:** [Chapter 4: Tungsten & TiN Etch Chemistry — Fluorine, Chlorine & Selectivity](./04-w-tin-etch-chemistry.md)

---

**Chapter 3 Development Status:** Complete  
**Version:** 1.0
