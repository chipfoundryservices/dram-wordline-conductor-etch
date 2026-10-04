# Preface: The Etch That Places the Gate Edge

## Why This Book Exists

Most metal etches are judged by the line they leave on the wafer. An aluminum interconnect must keep its width, its sidewall, and its corrosion resistance, and the dielectric around it is deposited later. The DRAM buried word line is different. Its conductor is never patterned from the side. It is poured into a trench that already exists, polished flat, and then etched *down* inside the trench until its top surface reaches a depth the transistor needs. Nothing about the etch is lateral except what goes wrong. The only dimension it controls is one height, and that height is the gate edge of every access transistor in the chip.

DRAM word-line recess became a defining process when the industry moved to the **buried-channel array transistor** and the **6F² cell**. The word line stopped being a polysilicon–tungsten gate stack patterned on top of the silicon and became a metal rod buried inside it. The top of the rod sits beside the storage-node junction, separated only by the gate oxide. If it sits too high, the gate overlaps the junction, the field at the overlap drives band-to-band tunnelling, and gate-induced drain leakage drains the stored charge. If it sits too low, the channel ends before it reaches the junction, and the lightly doped gap in between adds resistance that the write current must cross in a few nanoseconds. Between these two failures lies a window about 10 nm deep.

The method, a timed metal etchback, looks routine. It asks a great deal of the plasma etch:

1. **Depth without a stop layer.** The recess ends in the middle of a homogeneous metal rod. Nothing changes in the plasma when the surface passes the target, so depth is set by time, by the incoming height after CMP, and by the stability of the chamber.

2. **Depth that does not depend on width.** The recess digs its own slot as it goes. By the end, the hole above the metal is 90 nm deep and 11 nm wide, and the rate at the bottom has fallen by a quarter. A word line 1 nm wider ends about 0.9 nm deeper, and the wide word-line ends at the array edge end almost 10 nm deeper.

3. **Two metals at one rate.** Tungsten forms volatile WF₆ with fluorine at room temperature. TiN forms TiF₄, which is not volatile below about 280 °C, and etches readily only in chlorine. The two must recess together to within about 3%, or the TiN is left as a thin wall above the tungsten or is pulled into a slit beside it.

4. **A seam that leads down.** The tungsten fills the slot by growing in from both walls, and the two fronts meet along a seam. When the recess reaches the seam, fluorine enters it and etches downward faster than the surface. The top of the conductor turns into a V.

5. **An oxide that must not notice.** The gate oxide on the wall above the recess is exposed for the whole etch. It lies next to the storage-node junction, where the field is highest. Thinning, fluorine incorporation, charging, and tungsten on its surface all show up as leakage.

6. **Walls coated with metal.** About one-sixth of the wafer surface is exposed metal. The tungsten and titanium leave the wafer as halides and oxyhalides, some of which condense on the chamber walls. Those deposits change the radical balance of the next wafer and can flake back onto it.

This book treats the word-line recess as a **precision metal etch in its own right**, not as a blanket etchback that happens to run inside a trench.

---

## Unique Aspects of DRAM Word-Line Conductor Etch

### 1. The Surface Is the Feature

In most etch steps, the critical dimension is lateral. In word-line recess, the critical dimension is the depth of one surface. Engineers talk about the recess depth from the silicon surface, the gate-to-junction overlap, and the TiN–W step. A recipe that changes the recess by 2 nm changes the GIDL of every cell in the array by a measurable factor.

### 2. Two Metals in One Slot

The slot holds a tungsten core 7 nm wide between two TiN walls 2 nm thick. The chemistries that suit each metal are different, and the balance between them sets the shape of the surface that the cap must cover. No single gas etches both metals at the same rate across the range of temperature, wall state, and depth that production sees.

### 3. Width Becomes Depth

The recess has no mask of its own. The slot it etches into is defined by the word-line trench, the gate oxide, and the TiN. Every error in those widths turns into a depth error through ARDE. The wide word-line ends, pads, and dummy lines recess faster than the dense array beside them.

### 4. No Etch Stop, and No Signal

The exposed metal area stays constant while the recess deepens. Optical emission shows no transition at the target. Depth is controlled by time, by feed-forward from the post-CMP height, and by feedback from scatterometry and electrical tests.

### 5. The Etch Lives Next to the Junction

The gate oxide above the recess, the corner where the metal top meets the oxide, and the silicon behind the oxide make up the gate edge of the cell transistor. Plasma damage there does not stay in the etch module. It appears weeks later as a retention tail and a reliability risk.

---

## Why This Book Is Organized This Way

Book #27 follows the same four-part structure as Books #19–26:

**Part I: Fundamentals (Chapters 1–4)**
- Why the buried word line needs a recess and what sets its depth, how the conductor stack is built, the physics of metal recess in a narrow slot, and the chemistry of tungsten and TiN etch

**Part II: Hardware (Chapters 5–9)**
- The reactors, bias and pulsing systems, gas balance and recipe structure, temperature and chuck control, and wall, edge, and contamination management that let one chamber recess two metals evenly across a wafer

**Part III: Phenomena (Chapters 10–14)**
- Recess depth and overlap, TiN–W differential recess, seams and the top surface, oxide damage and retention, and advanced word-line schemes

**Part IV: Production (Chapters 15–16)**
- Endpoint, metrology, APC, the integration steps that use the recessed conductor, yield, and cost

### Reading Paths

**Process Engineers:** Chapters 3, 4, 7, 10, 11, 12  
→ Recipe design, depth control, TiN–W step, seam opening

**Equipment Engineers:** Chapters 5–9, 15  
→ Reactor selection, pulsing, gas and temperature control, chamber walls, endpoint hardware

**Integration Engineers:** Chapters 1, 2, 10, 11, 14, 16  
→ Overlap window, incoming stack and CMP, cap fill, dual-work-function gates, downstream steps

**Device Engineers:** Chapters 1, 10, 13, 16  
→ How recess errors become GIDL, retention tails, write failures, and word-line delay

**Researchers:** Chapters 3, 4, 6, 12, 13, 14  
→ Slot transport, halide volatility, atomic-layer recess, seam physics, damage, next-generation word lines

---

## Key Questions This Book Answers

1. **Why does the depth of the word-line recess decide both GIDL and write speed, and how wide is the window?**
2. **Why does the recess slow down as it deepens, and how much does word-line CD change the final depth?**
3. **Why do tungsten and TiN etch at different rates, and how can they be brought level?**
4. **What does a TiN horn or a TiN slit do to the cap, the contact, and the transistor?**
5. **Why does the tungsten seam open into a V, and how can the recess be made seam-tolerant?**
6. **What does the recess plasma do to the gate oxide above the metal, and how is that seen in retention?**
7. **How is recess depth controlled without an etch stop or a usable endpoint at the target?**
8. **How do dual-work-function gates, molybdenum and ruthenium word lines, 4F² vertical-channel cells, and 3D DRAM change the conductor etch?**
9. **What does the recess cost per wafer, and how does that compare with what it costs when it goes wrong?**

---

## How to Read This Book

**Complete study (2–3 weeks):** Read Part I closely, then work through Parts II and III in order. Finish with Part IV.

**Focused study (3–5 days):** Read Chapters 1 and 3, then follow the reading path for your role.

**Reference mode:** Go straight to the chapter you need. Use the INDEX, GLOSSARY, and the Appendix G troubleshooting guide.

**Every chapter includes:**
- Learning objectives
- Quantitative models with worked numerical examples
- Representative production values, labelled as illustrative where appropriate
- Summary and key takeaways
- Study questions

**Appendices provide:**
- A: Metal, dielectric, and chamber material properties
- B: Etch chemistry and reaction data
- C: Standard operating procedures
- D: Process windows and lookup tables
- E: Recess geometry, transport, and word-line resistance calculations
- F: Endpoint and metrology reference
- G: Troubleshooting guide

---

## A Note on Data and Depth

The relationships in this book (ion-enhanced metal etching, halide and oxyhalide volatility, free-molecular transport, sheath physics, size-dependent resistivity, band-to-band tunnelling) are well established in the literature. The specific numbers in recipes, tables, and worked examples are **representative**. They are chosen to be physically consistent and close to typical practice, but they are not qualified conditions for any particular tool, layout, or node. Where a value is illustrative, the text says so and shows the arithmetic, so readers can repeat the analysis with their own measurements.

Throughout the book, a **reference process** ties the examples together:

```
Reference device:      1b-class DRAM, 6F² cell, buried-channel array transistor
                       (BCAT); word-line pitch 34 nm, bit-line pitch 51 nm
                       (F = 17 nm, cell area 6F² = 1734 nm²)
Reference WL trench:   width at the Si surface w_t = 18 nm (normal to the WL),
                       near-vertical in the recess zone; bottom 140 nm deep in
                       the AA and 180 nm in the isolation (40 nm saddle fin);
                       30 nm SiO₂ hard mask above the Si surface
Reference gate stack:  gate oxide t_ox = 3.5 nm (radical oxidation + ALD)
                       → conductor slot w_s = 11 nm
                       TiN liner t_TiN = 2.0 nm (ALD); W core w_W = 7 nm (CVD),
                       with a seam on the slot centreline
Reference recess:      starts at the CMP plane (mask top, z = −30 nm); array
                       erosion + dishing 5 nm; target conductor top z_r = 60 nm
                       below the Si surface → recess R = 90 nm from the field
                       mask top (85 nm of metal in the array), aspect ratio ≈ 8
                       spec z_r = 60 ± 5 nm; TiN–W step |Δ_TW| ≤ 3 nm
Reference junction:    storage-node n⁺ junction depth x_j = 62 nm
                       → gate-to-junction overlap +2 nm at target
Reference conductor:   80 nm tall over the AA, 120 nm in the isolation
                       (≈ 108 nm effective); sub-word line 52 µm (1024 cells)
                       → R ≈ 267 Ω/µm, R_SWL ≈ 14 kΩ
Reference etch:        ICP conductor chamber, 13.56 MHz source + 13.56 MHz bias,
                       synchronized pulsing; BT NF₃/Ar 5 s; main recess
                       SF₆/Cl₂/N₂/Ar; trim Cl₂/Ar 6 s; open-area W/TiN rate
                       ER₀ = 180 nm/min; slot ARDE coefficient k = 0.035
                       → main recess ≈ 32 s
```

We assume you know basic plasma physics and the general behavior of blanket etchback from earlier books. We do **not** assume you know DRAM cell architecture, the buried-channel transistor, the chemistry of refractory-metal halides, the physics of GIDL, or the link between gate-edge damage and data retention.

---

## Organization of This Repository

1. **README.md**: overview, scope, file structure, cross-references
2. **PREFACE.md**: this document
3. **INDEX.md**: detailed chapter outline, reading paths, estimated times
4. **chapters/**: Chapters 1–16
5. **appendices/**: Appendices A–G
6. **GLOSSARY.md**: technical terminology

---

## Acknowledgments & Scope

Book #27 is part of the **ChipFoundryServices Technical Series**. It draws on:

- The published plasma etch literature on tungsten and TiN etch, halogen chemistry, metal etchback, ARDE, and pulsed plasmas
- Thermochemical data on refractory-metal halides and oxyhalides
- Classical results on free-molecular flow through channels (Knudsen, Clausing) and on size-dependent resistivity of thin metal lines (Fuchs–Sondheimer, Mayadas–Shatzkes)
- Published descriptions of buried word-line integration, GIDL, and retention physics
- Representative industrial practice for DRAM word-line modules
- The earlier books in this series, especially Books #22 and #26

It is a **technical reference for professionals**. Background in plasma processing is assumed.

---

## Final Thought

A buried word line is a tungsten rod seven nanometres wide, hidden in a slot in the silicon and repeated across the whole array. The recess etch decides where it ends. It must end at the same depth in billions of places, flat, with both metals level, beside an oxide the plasma has barely touched.

Mastering word-line conductor etch means seeing that **the top of the metal is the gate edge, the slot it digs sets its own rate, and every surface it exposes ends up next to the junction that sets retention**. This book is meant to build that understanding.

---

**Welcome to Book #27: DRAM Word-Line Conductor Etch — Buried Word-Line Metal Recess and Gate-Electrode Formation for Buried-Channel DRAM.**

---

**Preface Version:** 1.0  
**Last Updated:** 2026-10-04
