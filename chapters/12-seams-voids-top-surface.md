# Chapter 12: Fill Seams, Voids & the Conductor Top Surface

## Overview

The tungsten core of the word line was grown inward from both walls of the slot, and the two growth fronts met on the centreline (Chapter 2.3.2). The plane where they met, the **seam**, is less dense than the grains on either side, often contains a string of nanometre-scale voids, and is a fast path for fluorine. While the seam is buried, it does no harm. The recess exposes it, and from then on, every second of the etch drives some fluorine down the seam ahead of the descending surface. The top of the conductor stops being flat and becomes a V. Where the fill left a real void, the recess can open it into a cavity.

This chapter covers the seam and how the recess opens it, a simple model of the V-notch, what notches and opened voids do to resistance and the cap, how tungsten grains and the nucleation layer roughen the surface, and the fill and recipe choices that make the recess seam-tolerant.

**Learning Objectives:**
- Describe the structure of a CVD tungsten seam and why it conducts fluorine
- Estimate the penetration depth of fluorine into an open seam
- Predict the V-notch depth and width from lateral and vertical etch rates
- Explain how voids near the target depth become cavities and cap voids
- Relate grain structure and the nucleation layer to top-surface roughness
- Choose fill and recipe changes that reduce seam attack, and know their costs

---

## 12.1 The Seam

### 12.1.1 Structure

```
Plan view of the W core (along the word line), schematic:

  TiN │ W grains (columnar, from left wall) ┆ W grains (from right wall) │ TiN
      │ ◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣ ┆ ◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣◢◣ │
      │                                  ┆ ○  ○    ○   ○ ← nanovoids       │
                                         seam (grain-boundary plane)
```

The seam is a vertical plane along the full length of the word line. It is a grain boundary between two sets of columnar grains, and where the fronts did not quite meet, it contains small voids. Its effective open width, averaged along the line, is typically 0.2–1 nm. Fluorine and residual HF from the WF₆ fill are concentrated in it.

### 12.1.2 Why the Seam Etches Fast

Three effects add:

```
Effect                              Consequence
──────────────────────────────────────────────────────────────────────────
Low density, open volume            F atoms enter and react inside, below
                                    the surface
Grain-boundary bonding is weaker    Higher spontaneous reaction probability
Ions concentrated on the slot       Ion-enhanced etching strongest exactly
centreline (Chapter 3.5.4)          above the seam
```

---

## 12.2 Fluorine in an Open Seam

### 12.2.1 Penetration Depth

An open seam behaves like a very narrow slit of width δ. Fluorine entering it strikes its walls many times, and each wall strike has a small probability s of reacting. The fluorine flux decays with depth into the seam over a characteristic length:

```
Penetration length (diffuse slit, reacting walls; order of magnitude):
  λ ≈ δ / √s

s ≈ 0.01 (spontaneous F + W at 50 °C, illustrative)

  δ = 0.3 nm:  λ ≈ 3 nm
  δ = 0.5 nm:  λ ≈ 5 nm
  δ = 1.5 nm:  λ ≈ 15 nm  (voided seam)
```

Within about λ of the surface, the seam walls are etched spontaneously and the seam widens. Below that, little fluorine arrives.

### 12.2.2 The V-Notch Model

The surface moves down at the vertical rate ER_v (ion-enhanced, about 2.3–2.6 nm/s in the slot). The seam walls near the surface move sideways at the lateral spontaneous rate ER_ℓ. In steady state, the seam opens into a V that travels down with the surface:

```
Half-angle of the V:     tan θ ≈ ER_ℓ / ER_v
Depth of the V:          d_V ≈ λ (set by penetration)
Width of the V at top:   w_V ≈ 2 d_V tan θ

Reference main step (illustrative):
  Spontaneous F share of the W rate ≈ 25% of open-area 3.0 nm/s = 0.75 nm/s
  Reduced by ARDE in the slot (×0.78) and by N₂ passivation (×0.5):
    ER_ℓ ≈ 0.75 × 0.78 × 0.5 ≈ 0.29 nm/s
  ER_v ≈ 2.4 nm/s → tan θ ≈ 0.12 → θ ≈ 7°

  δ = 0.5 nm: d_V ≈ 5 nm → w_V ≈ 2 × 5 × 0.12 ≈ 1.2 nm
```

```
V-notch at the conductor top (reference):

         TiN│      W      │TiN
            │╲           ╱│
            │ ╲    ╱╲   ╱ │   ← surface (rough)
            │  ╲  ╱  ╲ ╱  │
            │   ╲╱ V  ╲   │      notch ≈ 1.2 nm wide, ≈ 5 nm deep
            │    ┆        │
            │    ┆ seam   │
```

### 12.2.3 What Makes the Notch Worse

```
Change                               Effect on the notch (illustrative)
───────────────────────────────────────────────────────────────────────────────
No N₂ in ME                          ER_ℓ ×2 → θ ≈ 14°; width ≈ 2.4 nm
Wafer +10 K                          ER_ℓ +25% (Ch. 8.1) → wider
F-rich main step (χ = 0.3)           Spontaneous share up → wider and deeper
Isotropic W step (no bias)           ER_v ≈ ER_ℓ → seam etched as a slot;
                                     d_V limited only by λ and time
Voided seam (δ = 1.5 nm)             d_V ≈ 15 nm; "seam punch-through"
Long queue before recess (HF in      Seam pre-etched; notch present from start
seam reacts with moisture)
```

The worst case is an isotropic tungsten step, used in some flows to correct a TiN pullback (Chapter 11.5). With no ions, the surface and the seam etch at the same spontaneous rate, and the seam opens into a slot as deep as the fluorine can reach.

---

## 12.3 What the Notch and Opened Voids Do

### 12.3.1 Resistance

```
Notch cross-section (reference): ≈ ½ × 1.2 nm × 5 nm = 3 nm²
W cross-section: 756 nm² → loss ≈ 0.4%   (negligible)

Seam punch-through, 15 nm deep and 3 nm wide:  ≈ 23 nm² → ≈ 3% of A_W;
  and the top 15 nm of the core is split into two halves with more
  surface scattering → R_SWL up ≈ 4–5%
```

A shallow notch costs almost nothing in resistance. A punch-through costs about as much as 4–5 nm of extra recess.

### 12.3.2 Metrology Bias

Optical scatterometry measures an average top surface. A notch lowers the average, so OCD reports the conductor as slightly deeper than its flat portions. The bias is small for the reference notch (about 0.3 nm) but grows with notch width. A recipe change that widens the notch will appear in OCD as a depth shift that is not real (Chapter 15).

### 12.3.3 The Cap

The nitride cap fills the notch with its ALD liner. A V 1–2 nm wide fills without voids, as long as it opens upward. A punch-through that is narrow at the top and wider below, because fluorine etched the seam voids into small cavities, may not fill. It leaves a void in the middle of the cap's bottom surface, along the word line. Unlike the keyhole void at the wall (Chapter 11.3.3), this void lies at the centre, away from the contacts, and is less likely to cause a short. It can still collect moisture or chemistry from later cleans.

### 12.3.4 Voids Near the Target Depth

A true void in the fill, left where the slot was re-entrant, is harmless if it lies well below the target. If it lies within a few nanometres of z_r, the recess front breaks into it:

```
Void just below the target:

 before break-in        after break-in             after cap
 │▓▓▓▓▓┆▓▓▓▓▓│          │       ┊     │            │ SiN  SiN  │
 │▓▓▓▓▓┆▓▓▓▓▓│ ← front  │▓▓▓▓╲  ╱▓▓▓▓│            │▓▓▓▓╲ ○╱▓▓▓▓│ ← void
 │▓▓▓▓ ○ ▓▓▓▓│          │▓▓▓▓ ◯ ▓▓▓▓▓│ ← cavity   │▓▓▓▓ ◯ ▓▓▓▓│   trapped
 │▓▓▓▓▓▓▓▓▓▓▓│          │▓▓▓▓▓▓▓▓▓▓▓│   etched   │▓▓▓▓▓▓▓▓▓▓▓│   under cap
```

Once fluorine enters the void, it etches the void's walls in all directions. A 3 nm void can grow to 6–8 nm in the remaining seconds of the main step. The cap's ALD liner may close its narrow opening before filling it, leaving a buried cavity at the conductor top. Such cavities appear as local resistance increases and as occasional word-line opens if they connect along the line.

Where do such voids sit? In the reference process, the word-line trench is near-vertical in the recess zone, and voids are rare above about 100 nm. A word-line trench etch that bows near the silicon surface, or a narrowing where the trench passes from silicon into the isolation oxide, can place voids in the recess zone. The incoming specification of Chapter 2.7 (no voids above z = 100 nm) is there to prevent this.

---

## 12.4 Grains, Nucleation Layer, and Roughness

### 12.4.1 Grain-Dependent Etching

The tungsten core has grains 3–6 nm across, in various orientations. Ion-enhanced etching is only weakly orientation-dependent, but the spontaneous part and the grain boundaries are not. The surface roughens as it descends:

```
Top-surface RMS roughness vs. recess depth (illustrative, reference ME):
  Recess depth:   10 nm    40 nm    85 nm
  RMS:            0.5 nm   0.8 nm   0.9 nm   (saturates near the grain scale)

Without N₂: RMS ≈ 1.4 nm at 85 nm (Chapter 4.5.1)
```

Roughness is part of the local depth term (±0.8 nm) in the budget of Chapter 10.

### 12.4.2 The Nucleation Layer

The boron-containing nucleation layer, about 1.5 nm thick, lies between the TiN and the bulk tungsten on each side. It is amorphous or fine-grained β-W, and it etches about 10–20% faster than the α-W core in fluorine:

```
Nucleation-layer groove:
  A narrow strip 1.5 nm wide etching faster forms a groove between the TiN
  and the W core. Its own aspect ratio grows quickly (1.5 nm wide), so ARDE
  self-limits it to ≈ 1–2 nm deep in the reference process.

  │TiN│nl│   W core   │nl│TiN│
  │ ▓ │╲ │            │ ╱│ ▓ │ ← grooves beside the TiN
```

The groove makes the TiN look slightly taller than it is relative to the tungsten core in cross-sections, and it adds a small amount of local depth variation at the wall, where the gate edge is.

---

## 12.5 Seam-Free Fill and Seam-Tolerant Recipes

### 12.5.1 Fill Options

```
Fill approach                    Seam                       Cost / risk
──────────────────────────────────────────────────────────────────────────────────
Conventional conformal CVD       Full-height seam           Reference
Inhibition-controlled bottom-up  Seam suppressed in upper   Process complexity;
  CVD (nitrogen-based inhibition part of the slot           nucleation control
  at the top delays growth there)
Dep–etch–dep                     Seam opened and refilled   Extra steps; W loss
                                 from below
Fluorine-free W (WClₓ precursors) Similar seam; less F in   Precursor cost; Cl
                                 the seam to drive attack   in the film
Post-fill anneal                 Partial seam closure by    Thermal budget on the
                                 grain growth               gate oxide
Alternative metals (Mo, Ru)      Different nucleation;      Chapter 14
                                 can fill with less seam
```

### 12.5.2 Recipe Choices

```
Recipe choice                    Effect on notch       Trade-off
──────────────────────────────────────────────────────────────────────────
N₂ in the main step              Halves ER_ℓ           Slightly lower rate
Lower wafer temperature          Lower ER_ℓ            Larger horns (Ch. 8)
Higher ion share (more bias)     Higher ER_v, lower θ  Oxide selectivity
Cl-rich main step                Lower spontaneous F   TiN–W balance moves
Avoid isotropic W steps          No seam slots         Pullback correction
                                                       must be done otherwise
Short queue CMP → recess         Less seam pre-etch    Scheduling
```

The reference process uses N₂, a chlorine-rich main step, moderate bias, and no isotropic tungsten step. Its notch is about 5 nm deep and 1–2 nm wide, within the specification (target ≤ 4 nm is met on most wafers when the seam is tight, δ ≈ 0.3–0.4 nm; limit ≤ 8 nm).

---

## 12.6 Signatures

```
Observation                                     Likely cause
──────────────────────────────────────────────────────────────────────────────
Notch widens across the wafer after a recipe    N₂ flow low; wafer warmer; more F
  or chamber change
Notch deep on some lots only                    Fill seam more open (deposition);
                                                long CMP queue
Isolated cavities at the conductor top          Voids in the fill near z_r
                                                (trench profile)
Grooves beside the TiN deepen                   Nucleation-layer change (thicker,
                                                more boron)
OCD depth shifts without electrical shift       Notch or roughness change biasing
                                                OCD (Ch. 15)
R_SWL up without OCD depth change               Punch-through or cavities
```

---

## 12.7 Summary & Key Takeaways

1. **The seam is a buried slit.** Conformal fill leaves a low-density grain-boundary plane with nanovoids along the slot centreline. The recess exposes it.

2. **Fluorine penetrates a few seam widths times 1/√s.** For a 0.5 nm seam, λ ≈ 5 nm. Within that depth the seam walls etch sideways.

3. **The notch angle is the lateral-to-vertical rate ratio.** With N₂ and a chlorine-rich main step, θ ≈ 7° and the notch is about 1.2 nm wide and 5 nm deep. An isotropic step turns the seam into a slot.

4. **Shallow notches are cheap; punch-through is not.** The reference notch costs 0.4% of W area. A 15 nm punch-through costs as much resistance as 4–5 nm of extra recess and can trap voids under the cap.

5. **Voids near the target become cavities.** Fluorine entering a void etches it out in all directions. The incoming fill must be void-free in the recess zone.

6. **Grains and the nucleation layer roughen the top.** RMS roughness near 1 nm and 1–2 nm grooves beside the TiN feed the local depth term of the budget.

---

## Study Questions

1. Compute λ for seam widths of 0.2, 0.5, and 1.0 nm with s = 0.01 and s = 0.03. Which change matters more for the notch depth: a tighter fill or a less reactive seam surface?

2. With ER_v = 2.4 nm/s, compute the notch half-angle and top width for ER_ℓ = 0.15, 0.29, and 0.6 nm/s, with d_V = 5 nm. At what ER_ℓ does the notch width reach the 7 nm core width?

3. A process uses an isotropic F-only W step of 4 s at 1.2 nm/s to correct a TiN pullback. For a seam with δ = 0.5 nm, estimate the seam opening depth and width after the step. Why is this worse than the same 4.8 nm removed by the reference main step?

4. A void of 3 nm diameter lies 4 nm below the target. The recess front reaches it with 1.7 s of main step remaining. If the void walls etch isotropically at ER_ℓ = 0.6 nm/s inside the void (no N₂ protection inside), compute the final cavity size. Will a 1.2 nm ALD liner close it before filling it?

5. OCD reports the array 0.8 nm deeper after a chamber clean, but R_SWL and GIDL test structures do not change. Propose two explanations based on this chapter and describe one measurement that distinguishes them.

---

**Next Chapter:** [Chapter 13: Gate-Oxide Integrity, Plasma Damage, GIDL & Retention](./13-oxide-damage-gidl-retention.md)

---

**Chapter 12 Development Status:** Complete  
**Version:** 1.0
