# Book #27: DRAM Word-Line Conductor Etch — Buried Word-Line Metal Recess and Gate-Electrode Formation for Buried-Channel DRAM

## Overview

**Book #27** is a technical reference on **DRAM word-line conductor etch**: the plasma etch that recesses the titanium nitride and tungsten of the buried word line (BWL) to a precise depth below the silicon surface, so that the gate electrode ends where the transistor needs it to end. In a modern 6F² DRAM the word line is buried in a trench about 18 nm wide, lined with 3.5 nm of gate oxide and 2 nm of TiN, and filled with a tungsten core about 7 nm wide. After CMP, the conductor reaches the top of the hard mask. The recess etch removes about 90 nm of metal from this 11 nm slot and stops, with no etch-stop layer, about 60 nm below the silicon surface. The tolerance is about ±5 nm, across billions of word-line segments on the wafer.

The recess etch is short, but it sets several device properties at once. The **height of the gate top** relative to the storage-node junction sets the gate-to-junction overlap. Too much overlap raises gate-induced drain leakage (GIDL) and lengthens the retention tail. Too little leaves an underlap that adds series resistance and slows writes. The **remaining conductor cross-section** sets word-line resistance and row access time. The **shape of the conductor top** sets how the silicon nitride cap fills above it. TiN left standing above the tungsten acts as a local high gate edge. TiN pulled below the tungsten leaves slits that the cap cannot fill, and the storage-node contact etch later breaks into them. The **gate oxide** on the trench wall above the recess must survive the etch, because it stays in the transistor next to the junction with the highest field in the cell.

The basic method is easy to state. Remove the native oxide and CMP residue from the metal surface. Etch tungsten and TiN together in a fluorine–chlorine plasma in an inductively coupled conductor chamber, at low ion energy so the gate oxide on the slot walls survives. Trim any TiN left above the tungsten with a short chlorine step. Stop on time, corrected by feed-forward from the post-CMP height. **The conductor top must land in a 10 nm window, flat, with TiN level with tungsten, on undamaged oxide, everywhere in the array.**

Doing it in production is hard. The recess hole deepens as the etch proceeds, so the etch rate falls with depth and depends on the slot width. Every nanometre of word-line CD becomes about 0.9 nm of recess depth. The wide word-line ends at the array edge and the sub-word-line drivers recess almost 10 nm deeper than the array. Tungsten etches easily in fluorine, but TiN does not, and the volatile chlorides and oxychlorides of the two metals behave very differently with temperature. The CVD tungsten core has a seam down its centre, and fluorine follows it. About one-sixth of the wafer surface is exposed metal, so etch products load the plasma and coat the chamber walls with tungsten and titanium compounds that change the next wafer's etch. This book covers the physics, chemistry, equipment, and production engineering that make DRAM word-line recess work.

---

## Intended Audience

This book is written for **semiconductor industry professionals** with working knowledge of plasma processing:

- **Process Engineers**: developing W/TiN recess recipes; controlling recess depth, TiN–W step, top-surface shape, seam opening, and array/edge loading
- **Equipment Engineers**: specifying inductively coupled conductor-etch chambers with pulsed source and bias, multi-zone temperature control, and metal-compatible wall materials; managing tungsten and titanium deposits, seasoning, and metal contamination
- **Integration Engineers**: setting recess depth against junction depth, word-line resistance, cap fill, and storage-node contact margin; designing the CMP–recess–cap sequence and its feed-forward
- **Device Engineers**: understanding how recess errors become GIDL, retention tails, write failures, row-hammer sensitivity, and word-line RC delay
- **Researchers**: studying metal etch in sub-15 nm slots, halide and oxyhalide volatility, atomic-layer metal recess, dual-work-function gates, molybdenum and ruthenium word lines, and word lines for 4F² vertical-channel and 3D DRAM

The material assumes a working knowledge of plasma physics (Books #1–5) and advanced plasma engineering (Books #11–15). Book #26 (DRAM Isolation Trench Etch) describes the cell array, the active areas, and the saddle fin that the word line wraps. The companion volume *DRAM Buried Word-Line Trench Etch* covers the trench that this conductor fills. The companion volumes *Aluminum Metal Etch* and *Polysilicon Etch* cover chlorine-based metal and silicon etch in a line-patterning context.

---

## Technical Scope

### Core Concepts Covered

**Architecture & Geometry:**
- The 6F² buried-channel DRAM cell: active areas, buried word lines, passing word lines, bit-line and storage-node contacts
- The buried word-line cross-section: trench, gate oxide, TiN liner, tungsten core, nitride cap
- Gate-to-junction overlap and the recess-depth window
- Word-line resistance, capacitance, and RC delay from the conductor cross-section

**The Incoming Stack:**
- Gate oxidation in the word-line trench; ALD TiN; CVD tungsten fill and its seam
- Tungsten CMP: dishing, erosion, and the starting height of the recess
- Etchback-only alternatives without CMP
- Array, array-edge, word-line end, and sub-word-line driver geometries

**Etch Physics & Chemistry:**
- Ion-enhanced metal etching; free-molecular transport in the recess slot
- ARDE of the recess, slot-width sensitivity, and global loading by exposed metal
- Fluorine chemistry for tungsten; chlorine chemistry for TiN; volatility of WF₆, WOF₄, WCl₆, WOCl₄, TiCl₄, and TiF₄
- Selectivity to gate oxide and nitride; N₂ and O₂ additives; residues

**Equipment Design:**
- Inductively coupled conductor chambers with independent source and bias
- Low ion energy, synchronized pulsing, and atomic-layer recess
- Gas delivery, F/Cl balance, and multi-step recipes
- Wafer temperature, multi-zone electrostatic chucks, and radial recess control
- Tungsten and titanium wall deposits, seasoning, and metal contamination

**Process Phenomena:**
- Recess depth, ARDE, and the gate–junction overlap window
- TiN–W differential recess: horns, pullback, and cap fill
- Seam opening, V-notches, voids, and the conductor top surface
- Gate-oxide attack, plasma-induced damage, fluorine incorporation, GIDL, and retention
- Advanced schemes: dual-work-function gates, molybdenum and ruthenium word lines, atomic-layer recess, 4F² vertical-channel and 3D DRAM word lines

**Production Integration:**
- Timed recess without a stop layer: feed-forward from CMP, endpoint for etchback clearing
- OCD scatterometry, STEM, AFM, and electrical word-line monitors
- Post-recess clean, nitride cap fill, cap CMP, and storage-node contact etch as customers
- Yield signatures, throughput, and cost of ownership

### Technology Context

- **Device architectures:** 6F² buried-channel array transistor (BCAT) DRAM from the 1x to the 1c generation (DDR5, LPDDR5X, HBM core dies); 4F² vertical-channel transistor (VCT) DRAM and 3D DRAM as emerging forms
- **Conductor structures:** TiN/W buried word lines (primary focus); dual-work-function TiN/W + n⁺ polysilicon word lines; molybdenum and ruthenium alternatives. Planar and recessed-channel stacked-gate word lines are covered where they explain the history
- **Process sequence:** The conductor recess follows word-line trench etch, gate oxidation, TiN and tungsten deposition, and tungsten CMP. It comes before the post-recess clean, nitride cap deposition, cap CMP, and the bit-line and storage-node contact modules
- **Manufacturing scale:** 300 mm wafers, one or two recess etches per wafer (two for dual-work-function gates), 35–45 s of metal etch inside a 2–3 min chamber cycle, a fleet of conductor-etch chambers per DRAM fab

---

## Book Organization

### Part I: Fundamentals (4 Chapters)

**Chapter 1: The DRAM Cell Array & the Role of the Buried Word-Line Conductor**
- The 1T1C cell and the buried-channel array transistor
- The four jobs of the conductor: gate edge, word-line wire, passing gate, cap foundation
- Gate-to-junction overlap, the recess window, and word-line RC
- Where the recess etch sits in the flow and the specification sheet

**Chapter 2: The Word-Line Conductor Stack — Gate Oxide, TiN, Tungsten Fill & CMP**
- Gate oxidation in the trench and the slot it leaves
- ALD TiN: thickness, work function, and composition
- CVD tungsten fill, nucleation, and the seam
- Tungsten CMP, dishing, erosion, and the starting height

**Chapter 3: Metal Recess Physics in Narrow Slots**
- Ion-enhanced metal etching and flux balance
- Free-molecular transport in a deepening slot
- ARDE of the recess, slot-width sensitivity, and wide word-line ends
- Global loading by exposed metal

**Chapter 4: Tungsten & TiN Etch Chemistry — Fluorine, Chlorine & Selectivity**
- Fluorine etching of tungsten; chlorine etching of TiN
- Volatility of halides and oxyhalides and the role of temperature
- Selectivity to gate oxide and nitride; N₂ and O₂ additives
- Breakthrough of tungsten oxide and CMP residue

### Part II: Hardware Design (5 Chapters)

**Chapter 5: Inductively Coupled Conductor Chambers for Word-Line Recess**
- Why ICP conductor chambers are used for metal recess
- Source and bias decoupling at low ion energy
- Pumping, residence time, and etch-product loading
- Throughput, fleet size, and chamber matching

**Chapter 6: Ion Energy, Pulsing & Atomic-Layer Recess**
- Ion energy for metal etch versus oxide damage
- Synchronized source and bias pulsing
- Ion angular distribution in an 11 nm slot
- Quasi-atomic-layer recess cycles

**Chapter 7: Gas Delivery, F/Cl Balance & Multi-Step Recess Recipes**
- Pressure, flow, and residence time
- The F/Cl ratio and TiN–W rate matching
- Breakthrough, main-recess, and trim steps
- Center/edge gas tuning

**Chapter 8: Wafer Temperature, Electrostatic Chucks & Radial Recess Uniformity**
- Temperature dependence of tungsten and TiN etch
- Heat balance and multi-zone chucks
- Radial tuning of recess depth and TiN–W step
- Thermal transients in short recipes

**Chapter 9: Chamber Walls, Metal Deposits, Seasoning & Contamination**
- Tungsten and titanium wall deposits and the first-wafer effect
- Waferless autoclean and seasoning
- Edge rings and edge recess
- Metal, particle, and fluoride-flake defects

### Part III: Process Phenomena (5 Chapters)

**Chapter 10: Recess Depth Control & the Gate–Junction Overlap Window**
- The depth budget and its contributors
- ARDE, slot-width, and pattern-density effects on depth
- Word-line ends, array edges, and sub-word-line driver pads
- Overlap, GIDL, and series resistance as functions of depth

**Chapter 11: TiN–W Differential Recess — Horns, Pullback & Cap Integrity**
- How a TiN–W step forms and grows
- TiN horns and the local gate edge
- TiN pullback, slits, and cap voids
- Trim strategies and rate matching

**Chapter 12: Fill Seams, Voids & the Conductor Top Surface**
- The CVD tungsten seam and how the recess opens it
- V-notches, seam etching, and buried voids
- Top-surface roughness and grain effects
- Seam-free fill and seam-tolerant recipes

**Chapter 13: Gate-Oxide Integrity, Plasma Damage, GIDL & Retention**
- Oxide thinning above the recess
- Fluorine and chlorine in the gate oxide; charging damage
- Metal redeposition on the trench wall
- How recess damage becomes GIDL, retention tails, and reliability loss

**Chapter 14: Advanced Schemes — Dual-Work-Function Gates, New Metals, ALE, 4F² & 3D DRAM**
- Dual-work-function word lines and the polysilicon recess
- Molybdenum and ruthenium word lines
- Atomic-layer and thermal recess
- Word lines for 4F² vertical-channel and 3D DRAM

### Part IV: Production Scale (2 Chapters)

**Chapter 15: Endpoint, Metrology & Advanced Process Control**
- Endpoint for breakthrough and etchback clearing; depth by time
- OCD scatterometry, STEM, AFM, and in-line monitors
- Electrical monitors of word-line resistance and GIDL
- Feed-forward and feedback APC

**Chapter 16: Post-Recess Integration, Yield & Cost of Ownership**
- Post-recess clean and queue time
- Nitride cap fill, cap CMP, and the contact modules
- Defect modes and yield signatures
- Throughput, consumables, and cost-of-ownership modeling

---

## Key Technical Themes

1. **The top of the metal is the gate edge.** The recess etch decides where the gate ends relative to the storage-node junction. A 10 nm window in depth is the window between write failures and retention failures.
2. **The slot deepens as you etch it.** The recess builds its own aspect ratio, so the rate falls with depth and every nanometre of word-line CD becomes about 0.9 nm of depth.
3. **Two metals, one surface.** Tungsten etches in fluorine and TiN etches in chlorine. A 3% rate mismatch over a 90 nm recess leaves a 3 nm step, and the step decides whether the cap fills.
4. **The seam is a channel.** The CVD tungsten core has a seam down its centre. Once the recess reaches it, the etchant follows it and the top surface becomes a V.
5. **The oxide above the metal stays.** The gate oxide on the slot wall above the recess is exposed to the whole etch. It must lose less than half a nanometre and carry no extra charge.
6. **Metal goes somewhere.** Every recess etch puts tungsten and titanium compounds on the chamber walls. The wall state changes the next wafer's recess, and metal that returns to the wafer becomes leakage.

---

## Cross-References to Prior Books

**Related Books in the Series:**

- **Books #1–5** (Plasma Physics & Chemistry Fundamentals): sheath physics, ion energy and angular distributions, radical generation and transport
- **Books #6–10** (Dielectric Etch & Fluorocarbon Chemistry): the hard-mask and cap-nitride etches around the word line
- **Books #11–15** (Advanced Plasma Engineering): ICP sources, RF delivery, pulsing, gas delivery, endpoint detection
- **Book #21** (Shallow Trench Isolation Etch): general isolation physics
- **Book #22** (Spacer Etchback): blanket etchback with timed overetch, the closest relative of the recess etch
- **Book #24** (3D NAND Slit Etch): the replacement-gate tungsten separation recess in 3D NAND
- **Book #26** (DRAM Isolation Trench Etch): the 6F² cell, active areas, and the saddle fin
- **Companion volumes:** *DRAM Buried Word-Line Trench Etch*, which forms the trench this conductor fills; *Aluminum Metal Etch*, which covers chlorine metal etch and corrosion; *Polysilicon Etch*, which covers the HBr/Cl₂ chemistry used for the dual-work-function polysilicon recess; *Silicon Nitride Etch*, which covers the cap nitride

Word-line recess takes the blanket etchback of Book #22 and applies it to two metals in an 11 nm slot, where the height of the surface left behind is the gate edge of every cell in the chip.

---

## File Organization

```
dram-wordline-conductor-etch/
├── README.md            ← You are here
├── PREFACE.md
├── INDEX.md
├── GLOSSARY.md
│
├── chapters/
│   ├── 01-dram-cell-wordline-architecture.md
│   ├── 02-wordline-conductor-stack.md
│   ├── 03-recess-etch-physics.md
│   ├── 04-w-tin-etch-chemistry.md
│   ├── 05-icp-conductor-chamber.md
│   ├── 06-ion-energy-pulsing-ale.md
│   ├── 07-gas-fcl-balance-steps.md
│   ├── 08-temperature-esc-radial.md
│   ├── 09-walls-metal-contamination.md
│   ├── 10-recess-depth-overlap.md
│   ├── 11-tin-w-differential-recess.md
│   ├── 12-seams-voids-top-surface.md
│   ├── 13-oxide-damage-gidl-retention.md
│   ├── 14-advanced-wordline-schemes.md
│   ├── 15-endpoint-metrology-apc.md
│   └── 16-integration-yield-coo.md
│
└── appendices/
    ├── A-material-properties.md
    ├── B-chemistry-reaction-data.md
    ├── C-standard-procedures.md
    ├── D-process-windows.md
    ├── E-recess-geometry-resistance-calculations.md
    ├── F-endpoint-metrology-reference.md
    └── G-troubleshooting-guide.md
```

---

## Constraints & Scope

### What This Book Covers
✅ TiN/W buried word-line recess etch for 6F² buried-channel DRAM (primary focus)  
✅ Dual-work-function polysilicon recess and alternative word-line metals  
✅ The incoming stack (gate oxide, TiN, tungsten fill, CMP) as the input to the etch  
✅ Equipment design, chamber control, and production integration  
✅ The processes that use the recessed conductor (clean, cap, contacts) as customers of the etch  
✅ GIDL, retention, write, row-hammer, and word-line RC impact; cost of ownership  

### What This Book Does NOT Cover
❌ The word-line trench etch itself, beyond what the conductor inherits (see the companion volume)  
❌ Isolation trench etch and active-area patterning (see Book #26)  
❌ Deposition and CMP process development in detail, beyond what the etch inherits  
❌ Bit-line, periphery-gate, and capacitor etches, and detailed DRAM circuit design  
❌ Vendor-specific recipes or proprietary tool parameters  

### A Note on Numbers
Numbers in this book come from established plasma physics, published literature trends, and representative production practice. Worked examples use **illustrative values** chosen to show the method, and the arithmetic is written out so readers can substitute their own data. A single **reference process** (a 1b-class 6F² array with 34 nm word-line pitch, 18 nm word-line trench, 3.5 nm gate oxide, 2 nm TiN, 7 nm tungsten core, a 90 nm recess from the CMP plane to 60 nm below the silicon surface, and a 62 nm storage-node junction) is used across chapters so that examples connect. The ARDE, TiN–W step, overlap, and resistance numbers in Chapters 3, 10, 11, and 13 come from closed-form models written out in Appendix E. Treat recipe values as starting points for a design of experiments, never as qualified process conditions.

---

## Development Status

**Book #27 Foundation:** Complete  
**Part I (Chapters 1–4):** Complete  
**Part II (Chapters 5–9):** Complete  
**Part III (Chapters 10–14):** Complete  
**Part IV (Chapters 15–16):** Complete  
**Back Matter (Appendices A–G, Glossary):** Complete  

---

## Next Steps

1. **Read [PREFACE.md](./PREFACE.md)** for the motivation and reading guidance
2. **Read [INDEX.md](./INDEX.md)** for the detailed chapter outline and reading paths by role
3. **Begin [Chapter 1](./chapters/01-dram-cell-wordline-architecture.md)**: The DRAM Cell Array & the Role of the Buried Word-Line Conductor

---

**Book #27 Version:** 1.0  
**Last Updated:** 2026-10-04  
**Series:** ChipFoundryServices Technical Series
