# Chapter 4: Tungsten & TiN Etch Chemistry — Fluorine, Chlorine & Selectivity

## Overview

The word-line recess has to etch two metals at one rate, beside an oxide it must not etch, and leave behind a surface clean enough to carry a nitride cap. Fluorine etches tungsten readily, because WF₆ is a gas at room temperature, but it hardly etches TiN, because TiF₄ is a solid until about 284 °C. Chlorine etches TiN readily, because TiCl₄ is a volatile liquid, but it etches tungsten slowly, because WCl₆ needs high temperature to leave the surface. Oxygen changes both: it makes the tungsten oxyhalides more volatile and the titanium oxyhalides less. The recess chemistry is built on these volatility facts.

This chapter covers the volatility map of tungsten and titanium products, fluorine etching of tungsten, chlorine etching of TiN, how mixing the two halogens sets the TiN–W rate ratio, the role of N₂, O₂, and Ar additives, selectivity to the oxide around the slot, the breakthrough of post-CMP oxide skins, and the residues the etch leaves. It ends with the reference recipe used through the book.

**Learning Objectives:**
- Use boiling and sublimation points to predict which products leave the surface at wafer temperature
- Describe the mechanisms of W etch in fluorine and TiN etch in chlorine
- Compute the TiN–W rate ratio as a function of the Cl fraction and the step it produces
- Explain the effects of N₂, O₂, and Ar additions
- Estimate oxide loss on the hard-mask top and on the slot walls
- Choose a breakthrough chemistry for post-CMP oxide skins
- Identify residues and their effect on the cap and on queue time

---

## 4.1 The Volatility Map

### 4.1.1 Products and Their Volatility

```
Product        Melting / boiling point          Volatile at 50 °C wafer?
                (at 1 atm)
───────────────────────────────────────────────────────────────────────────
WF₆            mp 2 °C, bp 17 °C                Yes, very
WOF₄           mp 101 °C, bp 186 °C             Partly (needs ions or heat)
WO₂F₂          Decomposes; not volatile         No
WCl₆           mp 275 °C, bp 347 °C             No (ion-assisted only)
WCl₅           mp 248 °C, bp 286 °C             No
WOCl₄          mp 211 °C, bp 228 °C             Weakly; better than WCl₆
WO₂Cl₂         Sublimes above ≈ 260 °C          No
TiCl₄          mp −24 °C, bp 136 °C             Yes
TiF₄           Sublimes ≈ 284 °C                No
TiBr₄          mp 39 °C, bp 230 °C              Weakly
TiOCl₂, TiO₂   Not volatile                     No
SiF₄           bp −86 °C                        Yes (oxide etch product)
SiCl₄          bp 58 °C                         Yes, but Cl hardly etches SiO₂
N₂             gas                              Yes (from TiN)
```

The pattern is simple. **Fluorine for tungsten, chlorine for titanium.** Oxygen helps tungsten in chlorine (WOCl₄ is more volatile than WCl₆) and hurts titanium in both halogens (titanium oxyhalides are not volatile).

### 4.1.2 Why Temperature Cannot Simply Be Raised

At 300 °C, TiF₄ would sublime and TiN would etch in fluorine, and WCl₆ would leave in chlorine. The recess cannot run that hot. The gate oxide and its interface are fine, but at that temperature fluorine diffuses along the tungsten seam and into the oxide faster, sulfur and chlorine move into the TiN, and the ESC and chamber parts are outside their normal range. Recess chemistry works between about 20 and 80 °C and uses the halogen mix, not the temperature, to balance the two metals (Chapter 8 covers the temperature effects that remain).

---

## 4.2 Fluorine Etching of Tungsten

### 4.2.1 Mechanism

```
F adsorbs and fluorinates the surface:   W + xF → WFₓ(ads), x = 1–5
Final step to the volatile product:      WF₅(ads) + F → WF₆(g)
Ion role:                                breaks W–W bonds, mixes F into the
                                         top monolayers, removes WFₓ (x < 6)
                                         and WOₓFᵧ directly
```

Fluorine sources are SF₆ and NF₃. Both give F atoms readily in an ICP. CF₄ also etches tungsten, but its carbon forms a fluorocarbon film on the oxide walls and on the TiN, which changes the TiN–W ratio and leaves residue, so fluorocarbons are avoided in the main recess.

### 4.2.2 Rate Dependence

```
Open-area W rate in SF₆/Ar (illustrative, 8 mTorr, 50 °C):

  Bias (V_dc-equiv.)   0 (no bias)   30 V    60 V    100 V
  W rate (nm/min)      70            170     260     330

Spontaneous component ≈ 70 nm/min; the rest is ion-enhanced.
```

Even with no bias, fluorine etches tungsten at a meaningful rate. That spontaneous component is isotropic. In a recess it is harmless on the flat surface but it drives fluorine down the seam (Chapter 12). The ion-enhanced part is directional and dominates the rate at the bias levels used.

### 4.2.3 Sulfur from SF₆

SF₆ fragments include sulfur-rich species that can deposit elemental sulfur or sulfur fluorides on cold surfaces. On the wafer at 50 °C the sulfur re-evaporates or is etched, but some remains in the top monolayers of tungsten and as SOₓFᵧ on the oxide. NF₃ avoids sulfur but gives a hotter, more dissociated plasma and more nitrogen. Many recipes use SF₆ with N₂, which reacts with sulfur fragments to form volatile S–N species and reduces sulfur residue.

---

## 4.3 Chlorine Etching of TiN

### 4.3.1 Mechanism

```
TiN + 4Cl → TiCl₄(g) + ½N₂(g)

Surface steps:  Cl adsorbs on Ti sites, breaks Ti–N bonds; N leaves as N₂
                (or as NCl species at low temperature); TiClₓ is chlorinated
                to TiCl₄ and desorbs
Ion role:       moderate; mainly removes the N-rich and O-rich top layer
```

TiN etches spontaneously in Cl atoms at room temperature, slowly, and much faster with modest ion energy. Oxygen in the film forms TiOₓClᵧ, which does not desorb and must be sputtered. An ALD TiN with 8% oxygen etches 15–30% slower in chlorine than one with 2% oxygen (illustrative), and the top 0.5 nm oxidized by CMP and air etches slowest of all.

### 4.3.2 TiN in Fluorine

In pure fluorine plasma the TiN surface becomes TiF₃/TiF₄, which stays at 50 °C. Ions remove it by sputtering at a rate that depends strongly on energy and is low below about 50 eV. This is why the TiN rate in the SF₆/Ar column of Section 4.4 is low, and why it is so sensitive to the ion shadowing of Chapter 3.5.

### 4.3.3 Tungsten in Chlorine

Tungsten etches slowly in pure chlorine at 50 °C. The products WCl₅ and WCl₆ need ion help to leave. A small amount of oxygen speeds it up through WOCl₄. This is useful in the trim step (Chapter 7), where the goal is to remove TiN while barely touching tungsten.

---

## 4.4 Mixing the Halogens: The TiN–W Rate Ratio

### 4.4.1 The Mixing Curve

Define the chlorine fraction of the halogen feed as χ = Q(Cl₂) / [Q(Cl₂) + Q(SF₆)]. As χ rises, the tungsten rate falls and the TiN rate rises:

```
Open-area rates vs. χ (illustrative; total halogen 100 sccm, N₂ 20 sccm,
Ar 100 sccm, 8 mTorr, 700 W source, reference pulsed bias, 50 °C):

  χ       W (nm/min)   TiN (nm/min)   r = TiN/W
  ─────────────────────────────────────────────
  0.0       260            40           0.15
  0.2       240            90           0.38
  0.4       210           140           0.67
  0.6       180           175           0.97   ← reference main step
  0.8       120           190           1.58
  1.0        35           200           5.7
```

The two rates cross near χ ≈ 0.62. The reference main step runs at χ = 0.6, just on the tungsten-fast side.

### 4.4.2 From Rate Ratio to Step

If both metals recess from the same starting height and each etches only from the top, the step after a recess of depth R is:

```
Δ_TW = (TiN top) − (W top), positive when TiN stands above W

Δ_TW ≈ (1 − r) × R   (r = ER_TiN / ER_W in the slot)

Reference array, R = 85 nm:
  r = 0.97  →  Δ_TW = +2.6 nm  (horn)
  r = 0.95  →  Δ_TW = +4.3 nm
  r = 1.03  →  Δ_TW = −2.6 nm  (pullback)
```

The spec is |Δ_TW| ≤ 3 nm. A pure rate match would need r within ±3.5% everywhere on the wafer, at every depth, all the time. That is not achievable with one step. Near the crossover, r changes by about 2.3 per unit of χ:

```
  ∂r/∂χ ≈ (1.58 − 0.67) / 0.4 ≈ 2.3

  A 1% flow error in Cl₂ (0.6 sccm of 60): Δχ ≈ 0.0024 → Δr ≈ 0.006
  → ΔΔ_TW ≈ 0.5 nm over 85 nm
```

Flow accuracy alone is manageable. Larger effects come from TiN composition (Section 4.3.1), ion shadowing in the slot (Chapter 3.5.2), temperature (Chapter 8), and wall state (Chapter 9). The practical answer is a main step that runs slightly tungsten-fast, so the error always has one sign (a small horn), followed by a short trim that removes the horn laterally (Chapter 11).

### 4.4.3 Why the Ratio Changes in the Slot

The open-area ratio is not the slot ratio. In the slot, TiN sits in the shadowed corners and tungsten sits in the full ion flux at the centre. In a step that needs ions to remove TiN, the slot ratio falls with depth:

```
Illustrative: open-area r = 0.97; ion-assisted share of the TiN rate = 50%;
corner ion flux at end of recess = 60% of centre

  r_slot(end) ≈ 0.97 × [0.5 + 0.5 × 0.60] = 0.97 × 0.80 = 0.78
  Average over the recess ≈ 0.88 → Δ_TW ≈ (1 − 0.88) × 85 ≈ +10 nm
```

This is why horns appear in the slot even when the open-area rates are matched, and why chlorine-rich (more spontaneous TiN) chemistry is used. At χ = 0.6, the ion-assisted share of the TiN rate is much smaller than 50%. Chapter 11 measures the real slot ratio with cross-sections.

---

## 4.5 Additives

### 4.5.1 Nitrogen

```
N₂ effect (illustrative, 0 → 20 sccm in the reference mix):
  W rate:            −5%
  TiN rate:          −3%
  Seam attack:       reduced (nitrided surface layer slows spontaneous F etch)
  Top roughness:     RMS 1.4 → 0.9 nm
  Sulfur residue:    reduced (volatile S–N species)
```

Nitrogen forms a thin WNₓ or nitrogen-rich layer on the tungsten surface. This layer slows the spontaneous fluorine etch more than the ion-enhanced etch. That makes the etch more directional, which helps at the seam and keeps the surface smooth.

### 4.5.2 Oxygen

Small oxygen additions in SF₆ plasmas raise the free fluorine density, because oxygen scavenges SFₓ fragments that would otherwise recombine with F. Larger amounts oxidize the tungsten surface to WOₓFᵧ, which etches more slowly, and oxidize TiN to TiOₓNᵧ, which etches much more slowly. Oxygen therefore pushes the TiN–W ratio down (toward horns) and is usually kept out of the main recess. A little O₂ in the trim step helps by making the tungsten surface self-limiting while chlorine removes TiN.

### 4.5.3 Argon and Helium

Argon dilutes the halogen, steadies the plasma, and adds ion flux without adding chemistry. Its heavier ions sputter TiFₓ and WOₓFᵧ more effectively than lighter ions. Helium is used where lower-mass ions are wanted to reduce oxide damage (Chapter 6), at the cost of a lower ion-enhanced rate.

---

## 4.6 Selectivity to the Oxide

### 4.6.1 Where Oxide Is Exposed

```
Surface                         Exposure                  Allowed loss
──────────────────────────────────────────────────────────────────────────
SiO₂ hard-mask top (horizontal) Full ion flux, full       ≤ 5 nm (cap CMP stop)
                                radical flux, whole etch
Slot walls above the metal      Grazing ions, radicals,   ≤ 0.5 nm per wall
(gate oxide + ALD oxide)        product redeposition;     (gate edge, Ch. 13)
                                exposure grows with depth
Top corner of the AA (gate      Both of the above at the  No silicon exposed
oxide at the Si surface)        shoulder
```

### 4.6.2 Oxide Etch Rates

Fluorine etches SiO₂ only with ion help, and the yield falls quickly below about 50 eV. Chlorine hardly etches SiO₂ at these energies.

```
Open-area SiO₂ rate in the reference main step (illustrative): 4 nm/min
  W : SiO₂ selectivity = 180 / 4 = 45

Hard-mask top loss:
  BT (5 s, higher bias, NF₃):  ≈ 1.0 nm
  Main (32 s):                 32/60 × 4 ≈ 2.1 nm
  Trim (6 s, Cl₂, low bias):   ≈ 0.1 nm
  Total:                       ≈ 3.2 nm   (target ≤ 3, limit ≤ 5)
```

The slot walls see much less. Ions strike them at grazing incidence, where sputter yield is low, and radicals alone etch SiO₂ only slowly. A wall loss of 0.1–0.3 nm is typical. The risk is local. At the top corner of the AA, the gate oxide lies just under the shoulder where the hard mask meets the silicon, and the ion flux there is nearly normal.

### 4.6.3 The Silicon Behind the Oxide

Fluorine etches silicon spontaneously and fast. If any point of the gate oxide is thinned through (a pinhole, a weak spot at the shoulder, an oxide already damaged by CMP), fluorine reaches the silicon of the AA and etches a pit into the channel or the junction. The defect is invisible in cross-sections taken elsewhere, and it appears as a single-bit retention or leakage failure. Chlorine-rich chemistry reduces the risk, because chlorine etches silicon only with ion help.

---

## 4.7 Breakthrough of Post-CMP Skins

### 4.7.1 What Must Be Removed

```
Skin                        Thickness     Removed by
──────────────────────────────────────────────────────────────────────
WOₓ (WO₃, WO₂) on W         1–2 nm        F + ions (WOF₄); BCl₃ (O scavenger)
TiOₓNᵧ on TiN top           0.5–1 nm      Ions + Cl or BCl₃; slow in F
Slurry organics             < 1 nm        O-containing or Ar sputter
Fe, K residue               Sub-monolayer Clean before etch; partly by BT
```

### 4.7.2 Options

```
BT option             Rate on WOₓ   Effect on TiOₓNᵧ   Notes
───────────────────────────────────────────────────────────────────────────
NF₃/Ar, 100 V, 5 s    Good          Partial (sputter)  Reference; small oxide
                                                       loss on mask top
BCl₃/Cl₂, 80 V, 5 s   Good          Good               B residue; W start slow
CF₄/Ar, 100 V, 5 s    Good          Partial            Fluorocarbon on walls;
                                                       avoided
Ar only, 150 V, 5 s   Moderate      Good               Sputter redeposition on
                                                       walls; mask loss
```

An incomplete breakthrough leaves a delayed and uneven start. If the WOₓ is thicker in some places (longer queue, CMP non-uniformity), those places start late and end shallow. Because the metal area does not change at the target, this delay is not visible in emission and appears directly as depth error. Chapter 15 uses the queue time as a feed-forward input.

---

## 4.8 Residues and the Surface After Etch

### 4.8.1 What Remains

```
Residue                     Where                    Effect
──────────────────────────────────────────────────────────────────────────
WOₓFᵧ, WFₓ (sub-nm)         Metal top                Grows into WOₓ with air;
                                                     F released in queue
TiFₓ, TiOₓClᵧ               TiN top, corners         Poor cap nucleation;
                                                     corner voids
Cl, F adsorbed              All surfaces             HF/HCl with moisture;
                                                     corrosion, haze
W/Ti redeposit              Slot walls above metal   Leakage path on gate
                                                     oxide (Ch. 13)
S                           Metal top, walls         Cap adhesion
```

### 4.8.2 Post-Treatment

A short in-situ post-treatment after the trim removes adsorbed halogen and stabilizes the surface before the wafer leaves vacuum:

```
PT option            Effect
──────────────────────────────────────────────────────────────────────
N₂ or N₂/H₂ plasma,  Removes F/Cl as volatile species; nitrides the W top
no bias, 8 s         (≈ 0.3 nm); slows air oxidation in queue
O₂ plasma            Removes S and C; oxidizes W top (≈ 1 nm WOₓ) — must
                     then be reduced or removed before cap
H₂O vapor / thermal  Hydrolyzes halides; risk of HF on the wafer
```

The reference process uses an N₂/H₂ post-treatment and a queue-time limit to the post-recess clean and the cap deposition (Chapter 16).

---

## 4.9 The Reference Recipe

```
Step   Gas (sccm)                 p (mTorr)  Source (W)  Bias            Time    ESC (°C)
                                                                                 ctr/edge
─────────────────────────────────────────────────────────────────────────────────────────────
BT     NF₃ 20 / Ar 100            8          500         100 V eff., CW  5 s     50 / 52
ME     SF₆ 40 / Cl₂ 60 /          8          700         60 V eff.,      ≈ 32 s  50 / 52
       N₂ 20 / Ar 100                                    sync pulsed     (APC)
                                                         1 kHz, 50%
TR     Cl₂ 50 / Ar 150 / O₂ 2     15         600         ≤ 20 V eff.     6 s     50 / 52
PT     N₂ 150 / H₂ 50             30         800         none            8 s     50 / 52

χ (ME) = 60/100 = 0.6; open-area rates W 180, TiN 175 nm/min; SiO₂ 4 nm/min
(all values illustrative; a starting point for a design of experiments)
```

The main-step time is set by APC from the incoming height and chamber state (Chapter 15). The trim time is fixed. The step design is developed in Chapter 7.

---

## 4.10 Summary & Key Takeaways

1. **Volatility decides the chemistry.** WF₆ and TiCl₄ are volatile at wafer temperature. TiF₄ and WCl₆ are not. Fluorine etches tungsten, and chlorine etches TiN.

2. **The Cl fraction sets the TiN–W ratio.** In the reference mix, the rates cross near χ ≈ 0.62. A ratio error of 3% over an 85 nm recess makes a 2.6 nm step.

3. **The slot ratio is lower than the open-area ratio.** TiN sits in the ion-shadowed corners. The more its removal depends on ions, the more the slot creates horns.

4. **Additives are levers.** N₂ smooths the surface and slows seam attack. O₂ pushes toward horns in the main step but helps the trim. Ar adds sputtering.

5. **Selectivity is set by ion energy and fluorine.** The mask top loses about 3 nm, and the slot walls lose a few tenths of a nanometre. The risk is the silicon behind any weak spot in the gate oxide.

6. **The surface before and after matters.** Post-CMP oxide skins must be broken through evenly, and halogen residues must be removed before air exposure.

---

## Study Questions

1. Using the volatility table, explain why a TiN film etched in an SF₆/O₂ plasma at 50 °C develops a surface crust, and predict the effect of raising the wafer to 120 °C. Which product could leave at 120 °C that could not at 50 °C?

2. From the mixing table, interpolate the χ at which r = 1.00. If the main recess runs at that χ in open area, and the slot ratio is 8% lower on average, compute Δ_TW for an 85 nm recess. What χ would give Δ_TW = 0 in the slot?

3. A TiN deposition change raises the film oxygen from 3% to 7%, which lowers the TiN rate in the main step by 12%. Starting from r = 0.97, compute the new Δ_TW. How long a trim at a lateral TiN rate of 1.0 nm/s is needed to clear the horn, if the horn is 2.0 nm thick?

4. The breakthrough is shortened from 5 s to 3 s. The WOₓ skin is 1.6 nm, and the BT removes it at 0.4 nm/s. How long is the start of the main step delayed? Estimate the resulting z_r shift.

5. The hard-mask loss limit is 5 nm. With the main-step oxide rate at 4 nm/min, how much longer could the main step run before the mask loss exceeds the limit? Why is the slot wall loss not proportional to the mask loss?

---

**Next Chapter:** [Chapter 5: Inductively Coupled Conductor Chambers for Word-Line Recess](./05-icp-conductor-chamber.md)

---

**Chapter 4 Development Status:** Complete  
**Version:** 1.0
