# Chapter 1: The DRAM Cell Array & the Role of the Buried Word-Line Conductor

## Overview

A DRAM stores each bit as charge on a capacitor, reached through a single access transistor. The gate of that transistor is a segment of a **word line** (WL), a conductor that runs across the array and turns on every cell in one row at once. Since the 6F² buried-channel generation, the word line has been buried inside the silicon: a rod of tungsten with a titanium nitride liner, lying in a trench and insulated from the silicon by a thin gate oxide. Its top surface is recessed below the silicon surface and covered by a silicon nitride cap. The plasma etch that sets the height of that top surface is the subject of this book.

This chapter explains why the word line is buried, what the top of the conductor has to do for the transistor, the row, the neighboring cells, and the contacts above it, and how those jobs set the recess depth and its tolerance. It ends with the specification sheet that the rest of the book works to.

**Learning Objectives:**
- Describe the 1T1C cell, the 6F² layout, and the buried-channel array transistor
- Explain the four jobs of the word-line conductor: gate edge, word-line wire, passing gate, and cap foundation
- Compute the gate-to-junction overlap and the recess-depth window it implies
- Estimate word-line resistance, capacitance, and RC delay from the conductor cross-section
- Compute the recess depth, slot aspect ratio, and conductor height for the reference process
- Place the recess etch in the DRAM front-end flow and read its specification sheet

---

## 1.1 The 1T1C Cell

### 1.1.1 Storing a Bit

```
One DRAM cell:

        Bit line (BL)
            │
            │ bit-line contact (DC)
          ┌─┴─┐
   WL ────┤ T ├──── access transistor (buried-channel, n-type)
          └─┬─┘
            │ storage-node contact (BC)
          ══╪══ storage capacitor C_s (≈ 8 fF), plate at V_PL = V_DD/2
            │
           ───

Write:  WL raised to V_PP (≈ 2.9 V), BL driven to V_DD ("1") or 0 ("0")
Hold:   WL held at a negative level V_NWL (≈ −0.3 V); transistor off
Read:   BL precharged to V_DD/2; WL raised; charge sharing moves the BL by
        ΔV_BL = (V_DD/2) · C_s / (C_s + C_BL); the sense amplifier restores
```

The word line is the only gate the cell has. It must turn the transistor fully on, at a boosted voltage V_PP, to write a full level into the capacitor in a few nanoseconds. It must also hold the transistor off, at a slightly negative voltage, for 64 ms or longer while the capacitor sits at V_DD.

```
Reference values (illustrative):
  C_s = 8 fF, V_DD (array) = 1.1 V, plate at V_DD/2

  Charge relative to the plate:  Q = C_s · V_DD/2 = 8 fF × 0.55 V = 4.4 fC
                                  ≈ 27,500 electrons
  BL signal with C_BL = 40 fF:   ΔV_BL = 0.55 × 8/48 = 92 mV
```

### 1.1.2 The Retention Budget

The cell must be refreshed before it loses enough charge that the sense amplifier misreads it. With a 40% allowable signal loss and a 64 ms refresh interval:

```
  ΔQ_allowed = 0.4 × 4.4 fC = 1.76 fC
  I_max = ΔQ / t_REF = 1.76×10⁻¹⁵ C / 0.064 s = 2.8×10⁻¹⁴ A = 28 fA
```

Most cells leak far less. The refresh interval is set by a few thousand **tail cells** out of about seventeen billion. Book #26 traced part of that tail to defects on the isolation sidewall. This book traces another part to the **gate edge**: the place where the top of the word-line conductor faces the storage-node junction across 3.5 nm of oxide. Leakage there is gate-induced drain leakage (GIDL), and it depends steeply on how far the conductor overlaps the junction (Section 1.4.1, Chapter 13).

---

## 1.2 The Word Line in the 6F² Array

### 1.2.1 Layout

```
Reference array (illustrative 1b-class, as in Book #26):
  F = 17 nm
  Word-line pitch     = 2F = 34 nm
  Bit-line pitch      = 3F = 51 nm
  Cell area           = 6F² = 1734 nm²
  16 Gb die: ≈ 1.72×10¹⁰ cells; array ≈ 55% of a ≈ 54 mm² die
```

The word lines run straight across the array at a 34 nm pitch. The active-area (AA) islands are tilted about 20° from the bit-line direction, so each word line crosses AA lines at an angle. Along one AA line the crossings repeat with a period of three word lines: two cross the island and gate its two transistors, and the third passes through the cut gap between islands. Along a word line, the crossings fall into three kinds:

```
Along one word line (per bit-line pitch, 51 nm):
  AA line crossings:      51 nm / (32 nm / sin 70°) = 1.5 per BL pitch
  Of these, 2/3 land on an island → 1 gated transistor per BL pitch ✓
            1/3 pass through a cut gap → passing word line segment

Length of each crossing over silicon (AA width 14 nm, crossing at 70°):
  14 / sin 70° = 14.9 nm
Fraction of WL length over silicon:  14.9 / 51 ≈ 0.29
Fraction over isolation oxide:       ≈ 0.71
```

### 1.2.2 Sub-Word Lines and Drivers

A word line is not one wire across the chip. The array is divided into sub-arrays, and each **sub-word line** (SWL) is driven by a sub-word-line driver (SWD) placed in a strip at the edge of the sub-array. The reference sub-word line serves 1024 cells:

```
Sub-word-line length:  L_SWL = 1024 × 51 nm = 52.2 µm  (≈ 52 µm)
```

At the SWD end, each word line must be contacted from above. The buried word line widens into a **landing pad** or runs into a wider strap region, often 30–50 nm wide, where a contact can land on it. These wider regions are etched in the same recess step as the 11 nm array slot, and they recess differently (Chapters 3 and 10).

```
Plan view of one sub-array edge (schematic):

   SWD strip  │◄──────────── cell array ────────────►│
   ┌───┐      │                                      │
   │pad├──────┼══════════════════════════════════════┤  WL n   (11 nm slot)
   └───┘      │                                      │
        ┌───┐ │                                      │
        │pad├─┼══════════════════════════════════════┤  WL n+1
        └───┘ │                                      │
   ┌───┐      │                                      │
   │pad├──────┼══════════════════════════════════════┤  WL n+2
   └───┘      │                                      │
   pads staggered, ≈ 40 nm wide; contacts land on them after the cap
```

---

## 1.3 The Buried-Channel Array Transistor

### 1.3.1 Why the Word Line Is Buried

A planar access transistor with a gate length near F = 17 nm cannot keep subthreshold leakage at the femtoampere level. The buried-channel array transistor (BCAT) buries the word line in a trench that cuts across the AA and the isolation. Current flows down one side of the trench, under its bottom, and up the other side. The effective channel length becomes several times the word-line width.

### 1.3.2 The Cross-Section Along an Active Area

```
Cross-section ALONG an AA island, through two word lines
(z measured downward from the Si surface):

        BC               DC               BC
        ▼                ▼                ▼
 z=0 ───┬────┐      ┌────┴────┐      ┌────┬───   Si surface
        │ n⁺ │ ░░░░ │   n⁺    │ ░░░░ │ n⁺ │      ░ SiN cap
        │    │ ░░░░ │         │ ░░░░ │    │
 z=60 ──│────│─████─│─────────│─████─│────│──   conductor top (z_r)
 x_j=62 │╌╌╌╌│ ████ │╌╌╌╌╌╌╌╌╌│ ████ │╌╌╌╌│      n⁺ junction (BC side)
        │    │ ████ │         │ ████ │    │      █ TiN/W conductor
        │    │ ████ │         │ ████ │    │
 z=140 ─│    └──┬───┘         └───┬──┘    │──   WL bottom over the AA
        │   channel             channel   │
        └──────────── p-well ─────────────┘

Gate oxide (3.5 nm) lines every trench wall, from the bottom up to the
Si surface. The SiN cap fills the slot above the conductor.
```

The transistor's channel runs from the storage-node junction (BC side) down the trench wall, under the word line, and up to the bit-line junction (DC side). The gate controls only the part of the wall that faces the conductor. **The top of the conductor is the gate edge.** Above it, the wall faces the nitride cap, which has no potential of its own.

### 1.3.3 The Cross-Section Across the Word Line

```
Cross-section ACROSS the word line, over an AA (normal to the WL):

         │◄────────── w_t = 18 nm ──────────►│
 z=−30 ──┬───────────────────────────────────┬──  top of SiO₂ hard mask
         │ox│  │                       │  │ox│     (CMP plane, start of
 z=0   ──┤  │  │       SiN cap         │  │  ├──  recess)   Si surface
   Si    │  │  │                       │  │  │  Si
         │  │  │                       │  │  │
 z=60  ──┤  │  ├──┬─────────────────┬──┤  │  ├──  conductor top z_r
         │  │  │Ti│   W core 7 nm   │Ti│  │  │
         │  │  │N │       ┆ seam    │N │  │  │
         │  │  │  │       ┆         │  │  │  │
 z=140 ──┤  │  └──┴─────────────────┴──┘  │  ├──  WL bottom (AA)
         │◄►│◄►│                       │◄►│◄►│
       3.5 nm 2 nm                   2 nm 3.5 nm
          ox   TiN                    TiN   ox

  Conductor slot:  w_s = w_t − 2 t_ox = 18 − 7 = 11 nm
  W core:          w_W = w_s − 2 t_TiN = 11 − 4 = 7 nm
```

---

## 1.4 The Four Jobs of the Word-Line Conductor

### 1.4.1 Job 1: Gate Edge — The Overlap Window

The storage-node junction is an n⁺ region diffused down from the silicon surface at the island end. Its metallurgical depth on the trench wall, x_j, is set by implants and anneals long after the recess. The recess sets z_r, the depth of the conductor top. Their difference is the **gate-to-junction overlap**:

```
Overlap:   Δ_ov = x_j − z_r

  Δ_ov > 0  →  gate overlaps the n⁺ region by Δ_ov
  Δ_ov < 0  →  underlap: a gap of |Δ_ov| between the gate edge and the n⁺,
               bridged only by lightly doped silicon

Reference:  x_j = 62 nm, z_r = 60 nm  →  Δ_ov = +2 nm
```

Each sign of error has its own failure:

```
Too much overlap (recess too shallow, z_r small):
  The gate at V_NWL faces n⁺ silicon at V_DD across 3.5 nm of oxide.
  The field at the overlap corner drives band-to-band tunnelling (GIDL)
  and trap-assisted tunnelling. Leakage rises steeply with overlap.
  → retention tail, refresh failures

Too much underlap (recess too deep, z_r large):
  The channel ends below the junction. The ungated gap adds series
  resistance in the path of the write current.
  → slow write (tWR failures), lower read signal development
```

A simple illustrative model captures both sides:

```
Illustrative device sensitivities (representative of published trends):

  GIDL:  I_GIDL(Δ) = I_GIDL(+2) × 10^((Δ − 2)/8)     (one decade per 8 nm)
  I_on:  I_on(Δ)   = I_on,0 × [1 − 0.04 × max(0, −Δ)] (−4% per nm underlap)

  Limits (illustrative): I_GIDL ≤ 4.2 × I_GIDL(+2)  → Δ ≤ +7 nm
                         I_on   ≥ 0.88 × I_on,0      → Δ ≥ −3 nm

  Window in Δ:     −3 nm ≤ Δ_ov ≤ +7 nm
  Window in z_r:   x_j − 7 ≤ z_r ≤ x_j + 3  →  55 nm ≤ z_r ≤ 65 nm
  Target:          z_r = 60 ± 5 nm
```

The window is only 10 nm wide, and it must contain the recess-etch variation, the incoming CMP variation, and the variation of x_j itself. Chapter 10 builds the full budget.

### 1.4.2 Job 2: Word-Line Wire — Resistance and Delay

The conductor that remains after the recess carries the word-line current from the driver to the last cell on the sub-word line. Its height is the trench bottom minus z_r: 140 − 60 = 80 nm over the AA and 180 − 60 = 120 nm in the isolation. Using the length fractions of Section 1.2.1:

```
Effective conductor height:  h_eff = 0.29 × 80 + 0.71 × 120 = 108 nm

Cross-sections (rectangular approximation):
  W core:  A_W   = 7 nm × 108 nm               = 756 nm²
  TiN:     A_TiN = 2 × 2 nm × 108 nm + 2 × 11  ≈ 454 nm²  (two walls + bottom)

Resistivities (illustrative; size effects included, Appendix A):
  ρ_W   = 22 µΩ·cm   (7 nm CVD W core; bulk 5.3 µΩ·cm)
  ρ_TiN = 150 µΩ·cm  (ALD TiN)

Resistance per micrometre:
  R_W   = ρ/A = 2.2×10⁻⁷ Ω·m / 7.56×10⁻¹⁶ m² = 291 Ω/µm
  R_TiN = 1.5×10⁻⁶ / 4.54×10⁻¹⁶             = 3300 Ω/µm
  Parallel:  R′ = 1 / (1/291 + 1/3300)       = 267 Ω/µm

Sub-word line:  R_SWL = 267 × 52 µm ≈ 13.9 kΩ   (≈ 14 kΩ)
```

The capacitance of the sub-word line comes from the gate oxide over the channel, the coupling to neighboring word lines, and the coupling to bit-line and storage-node contacts. An illustrative value is C_SWL ≈ 150 fF. The distributed RC delay to the far end is about 0.38 R C:

```
  t_RC ≈ 0.38 × 13.9 kΩ × 150 fF ≈ 0.79 ns
```

Every nanometre of extra recess removes about 1/108 of the conductor:

```
  ∂R/∂z_r ≈ R / h_eff = 13.9 kΩ / 108 nm ≈ 0.13 kΩ per nm   (+0.9%/nm)
  Over-recess of 5 nm → R_SWL ≈ 14.6 kΩ (+4.8%)
```

This is a weaker constraint than the overlap, but it is not free. It also shows why the recess does not simply go deeper to kill GIDL: every nanometre is taken from the wire.

### 1.4.3 Job 3: Passing Gate — Row Hammer

Where a word line passes through a cut gap, it runs in the isolation beside the end of an island it does not control, close to that island's storage-node junction. When the passing word line is repeatedly raised to V_PP and lowered, it couples to the neighbor's junction and to the silicon beneath it, and it pumps electrons that discharge the neighbor's capacitor. This is one mechanism of **row hammer**. The conductor top height matters here in the same way as for the gate edge. A higher top brings the passing gate's field closer to the neighbor's n⁺ region and increases the disturbance per activation. Deeper recess, lower-work-function material at the top of the word line (Chapter 14), and a thicker oxide at the passing-gate corner all reduce it.

### 1.4.4 Job 4: Cap Foundation — The Surface Under the Nitride

After the recess, the slot above the conductor is filled with silicon nitride and polished. The cap must isolate the word line from the storage-node contact (BC) and the bit-line contact (DC), which are etched down beside and over it later. The cap can only be as good as the surface it is deposited on:

```
Surface defect           What happens to the cap               Consequence
───────────────────────────────────────────────────────────────────────────────
TiN horn (TiN above W)   Cap is thinner over the horn tip;     WL–BC leakage, local
                         horn tip is a local high gate edge    GIDL hot spot
TiN pullback (slit)      2 nm slit beside the W is not filled; WL–BC short when the
                         keyhole void in the cap               BC etch opens the void
Opened seam / V-notch    Cap fills the V; conductor thinner    R_WL up; cap seam
                         at the centre                         defects
Residue on the oxide     Poor cap adhesion; trapped charge     Leakage, reliability
```

Chapter 11 treats the TiN–W step and Chapter 12 treats the seam.

---

## 1.5 Geometry of the Recess

### 1.5.1 Depth and Aspect Ratio

The recess starts at the CMP plane, which is the top of the 30 nm SiO₂ hard mask left from the word-line trench etch, and ends at z_r = 60 nm below the silicon surface:

```
Recess depth:          R = 30 + 60 = 90 nm
Slot width:            w_s = 11 nm
Final aspect ratio:    A_end = R / w_s = 90 / 11 = 8.2

Array erosion (2 nm) and dishing (3 nm) after CMP put the array metal top
5 nm below the field mask top (Chapter 2.4.3)
  → metal actually removed in the array: 85 nm
  → final hole depth in the array: 28 + 60 = 88 nm, aspect ratio 8.0
```

The aspect ratio starts near zero and rises to 8.2 as the etch proceeds. Unlike a trench etch, the recess has no mask whose erosion matters. Its "mask" is the dielectric around the slot: the SiO₂ hard mask above the silicon surface and the gate oxide below it. The walls of the hole it digs are the gate oxide that must survive (Chapter 13). In the reference stack the slot is slightly wider (13.8 nm) where it passes through the hard mask, because the grown part of the gate oxide forms only on silicon (Section 2.1.3). The models in this book use 11 nm throughout unless stated, which slightly overstates ARDE in the first 30 nm.

### 1.5.2 Where the Conductor Sits

```
Depth z (nm)     Feature
──────────────────────────────────────────────────────────
  −30            Top of SiO₂ hard mask; CMP plane; recess starts
    0            Si surface
   55            Shallowest allowed conductor top (Δ_ov = +7)
   60            Target conductor top z_r
   62            Storage-node junction depth x_j
   65            Deepest allowed conductor top (Δ_ov = −3)
  140            WL bottom over the AA (top of saddle fin)
  180            WL bottom in the isolation (saddle-fin bottom)
```

### 1.5.3 Generational Trend

```
Generation   WL pitch   WL trench   Gate ox   Slot w_s   Recess R   A_end   Window
(class)      (nm)       w_t (nm)    (nm)      (nm)       (nm)               (nm)
────────────────────────────────────────────────────────────────────────────────────
2x           ~52        ~28         ~5.5      ~17        ~95        ~5.6    ~±8
1x           ~42        ~23         ~4.5      ~14        ~95        ~6.8    ~±7
1y/1z        ~38        ~20         ~4.0      ~12        ~92        ~7.7    ~±6
1a/1b        ~34        ~18         ~3.5      ~11        ~90        ~8.2    ~±5
1c/1d        ~30        ~16         ~3.2      ~9.6       ~88        ~9.2    ~±4
(illustrative; values vary by manufacturer)
```

The slot narrows with the pitch, but the recess depth hardly changes, because it is tied to the junction depth, and the junction cannot be made much shallower without raising contact resistance. The aspect ratio rises every generation, and the window shrinks. The dual-work-function gate (Chapter 14) is one response: it lets the gate edge sit higher without the GIDL penalty, which relaxes the window.

---

## 1.6 The Recess Etch in the Process Flow

### 1.6.1 Before the Etch

```
Step                                   Result
──────────────────────────────────────────────────────────────────────────
1. Isolation trench etch, fill, CMP    AA islands in oxide (Book #26)
2. WL hard mask and patterning         SAQP lines at 34 nm pitch
3. WL trench etch (Si + oxide)         18 nm trenches; 140 nm deep in the AA,
                                       180 nm in the isolation (companion
                                       volume)
4. Clean; gate oxidation               Radical oxidation + ALD: 3.5 nm SiO₂
5. TiN ALD                             2.0 nm conformal liner
6. W CVD (nucleation + bulk)           Fill of the 7 nm core; ≈ 60 nm
                                       overburden on the field
7. W/TiN CMP                           Polish to the SiO₂ hard mask;
                                       dishing ≈ 3 nm in the array
```

### 1.6.2 The Recess Etch

```
8. WL CONDUCTOR RECESS ETCH            Breakthrough + main recess + TiN trim
   (this book)                         to z_r = 60 nm below the Si surface
                                       (≈ 45 s of plasma)
```

### 1.6.3 After the Etch

```
Step                                   What it needs from the etch
──────────────────────────────────────────────────────────────────────────
9.  Post-recess clean                  Removable residue; metal top that does
                                       not corrode or oxidize in queue
10. SiN cap deposition (ALD + CVD)     A flat metal top, TiN level with W, no
                                       slits; clean oxide walls
11. Cap CMP; hard-mask removal         Uniform cap thickness above the WL
12. Source/drain implants, anneals     The x_j that the overlap is measured to
13. DC (bit-line contact) etch         Cap thick enough over the WL;
                                       no voids
14. BC (storage-node contact) etch     Cap with no keyhole voids beside the W;
                                       no horns near the BC
15. WL contact at SWD pads             Pad recess not too deep for the contact
```

Every one of these customers sees a different part of the recessed conductor. The cap sees the surface shape, the contacts see the cap, the transistor sees the height, and retention sees the oxide above it.

---

## 1.7 The Specification Sheet

```
Parameter                          Target        Limit (illustrative)     Customer
─────────────────────────────────────────────────────────────────────────────────────────
Conductor top depth z_r (array)    60 nm         55–65 nm (3σ)            Overlap: GIDL /
                                                                          I_on; row hammer
z_r at SWD pads (≥ 30 nm wide)     ≤ 72 nm       ≤ 75 nm                  WL contact
z_r at array edge (first 3 WLs)    60 nm         55–67 nm                 Edge cells
TiN–W step Δ_TW (TiN top − W top)  0 nm          −3 to +3 nm              Cap fill, GIDL
Seam V-notch depth (below top)     ≤ 4 nm        ≤ 8 nm                   R_WL, cap
Top-surface roughness (RMS)        ≤ 1 nm        ≤ 1.5 nm                 Cap, metrology
Gate-oxide loss above the recess   ≤ 0.3 nm      ≤ 0.5 nm per wall        GIDL, TDDB
Hard-mask loss (SiO₂)              ≤ 3 nm        ≤ 5 nm                   Cap CMP stop
Within-wafer z_r range             ≤ 4 nm        ≤ 6 nm                   Window
Sub-WL resistance                  13.9 kΩ       ≤ 15.0 kΩ                tRCD, tWR
Residue (W/Ti oxyhalides)          —             None after clean         Cap adhesion
Metal on oxide walls               —             < 1×10¹⁰ cm⁻² (W, Ti)    Leakage
Defects (particles, flakes)        —             Within module budget     Yield
```

**No item on this sheet is about the etch alone.** Each one is a requirement passed back from the transistor, the wire, the cap, or a contact that comes later.

---

## 1.8 Summary & Key Takeaways

1. **The word line is buried, and its top is the gate edge.** In the BCAT, the gate controls the trench wall only below the conductor top. The recess etch sets where that is.

2. **Overlap is a two-sided window.** Δ_ov = x_j − z_r. Too much overlap raises GIDL and the retention tail; too much underlap adds resistance and slows writes. The reference window is −3 to +7 nm, so z_r = 60 ± 5 nm.

3. **The conductor is also the wire.** The reference sub-word line has R ≈ 14 kΩ and an RC delay near 0.8 ns, and each nanometre of extra recess adds about 0.9% to R.

4. **The passing gate and the cap also depend on the top.** Recess height affects row-hammer coupling, and the shape of the top surface (horns, slits, seams) decides whether the nitride cap protects the word line from the contacts.

5. **The recess is a 90 nm etch in an 11 nm slot.** Its aspect ratio rises to 8.2 by the end, and the slot narrows every generation while the depth does not.

6. **Every customer is downstream.** The cap, the contacts, the transistor, the word-line driver, and the retention screen each read a different property of one etched surface.

---

## Study Questions

1. A cell has C_s = 7 fF and V_DD = 1.05 V, with the plate at V_DD/2. The sense margin allows a 35% signal loss. Compute the maximum average leakage for a 32 ms refresh interval. If GIDL at the target overlap is 0.2 fA for a median cell, by what factor could GIDL rise before it alone used the budget?

2. A new node has x_j = 58 nm, and the device team gives the limits Δ_ov ≤ +6 nm (GIDL) and Δ_ov ≥ −2.5 nm (I_on). Compute the z_r window and its centre. If the recess must start 28 nm above the silicon surface, what is the recess depth at target?

3. Using the illustrative model of Section 1.4.1, compute the GIDL ratio and the I_on ratio at z_r = 54, 57, 60, 63, and 66 nm. Which limit fails first on each side?

4. For the reference cross-section, compute R′ (Ω/µm) when z_r = 66 nm, and the percentage change in R_SWL. Repeat with a 6 nm W core (TiN unchanged, slot 10 nm). Which change matters more, and why?

5. The SWD landing pad is 40 nm wide. Without any rate model, explain why a wider opening might recess faster than the 11 nm array slot. What problem does a deeper pad recess cause for the word-line contact, and what does a shallower one cause?

---

**Next Chapter:** [Chapter 2: The Word-Line Conductor Stack — Gate Oxide, TiN, Tungsten Fill & CMP](./02-wordline-conductor-stack.md)

---

**Chapter 1 Development Status:** Complete  
**Version:** 1.0
