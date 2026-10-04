# Index: Book #27 Navigation Guide

## Quick Navigation

**Total Content:** 16 chapters + 7 appendices + glossary  
**Estimated Read Time:** 22–30 hours for the complete book; 5–10 hours for a focused reading path

| Part | Chapters | Theme |
|------|----------|-------|
| I | 1–4 | Fundamentals: buried word-line architecture, the conductor stack and CMP, recess physics in narrow slots, W and TiN chemistry |
| II | 5–9 | Hardware: ICP conductor chamber, ion energy, pulsing and ALE, gas balance and recipe steps, temperature and ESC, walls and contamination |
| III | 10–14 | Phenomena: depth and overlap, TiN–W step, seams and the top surface, oxide damage and retention, advanced schemes |
| IV | 15–16 | Production: endpoint, metrology, APC, integration, yield, cost |

---

## Part I: Fundamentals (Chapters 1–4)

### Chapter 1: [The DRAM Cell Array & the Role of the Buried Word-Line Conductor](./chapters/01-dram-cell-wordline-architecture.md)
**Estimated Time:** 60 min | **Difficulty:** Foundation | **Reading Level:** All roles  
**Focus:** Why is the word line buried, and what must the recess deliver?

**Key Topics:**
- The 1T1C cell, the 28 fA retention budget, and the BCAT
- The four jobs: gate edge, word-line wire, passing gate, cap foundation
- Gate-to-junction overlap and the −3 to +7 nm window
- Word-line resistance (≈ 14 kΩ) and RC delay
- Recess geometry, generational trend, and the specification sheet

**Prerequisites:** None (foundational)  
**Cross-References:** Book #26 (cell array and AA)  
**Critical Equations:** Δ_ov = x_j − z_r; I_GIDL ∝ 10^(Δ/8); R′ = 1/(A_W/ρ_W + A_TiN/ρ_TiN); t_RC ≈ 0.38RC  
**Study Questions:** 5 calculations on retention, window, and resistance

---

### Chapter 2: [The Word-Line Conductor Stack — Gate Oxide, TiN, Tungsten Fill & CMP](./chapters/02-wordline-conductor-stack.md)
**Estimated Time:** 65 min | **Difficulty:** Intermediate | **Reading Level:** Process/Integration roles  
**Focus:** What does the recess inherit, and with what variation?

**Key Topics:**
- Grown and deposited gate oxide; slot 11.0 nm in Si, 13.8 nm in the mask
- ALD TiN composition and its effect on etch rate
- CVD W nucleation, conformal fill, the seam, size-dependent resistivity
- W CMP, dishing and erosion, starting height and its ±2.3 nm variation
- CMP-then-recess vs. etchback-only

**Prerequisites:** Chapter 1  
**Cross-References:** Appendix A, Appendix E.1  
**Critical Equations:** w_s = W₀ − 2(0.56t_g + t_d); H₀ = t_mask − erosion − dishing  
**Study Questions:** 5 calculations on slot, resistivity, and CMP

---

### Chapter 3: [Metal Recess Physics in Narrow Slots](./chapters/03-recess-etch-physics.md)
**Estimated Time:** 90 min | **Difficulty:** Advanced | **Reading Level:** Process/Research roles  
**Focus:** Why does the recess slow down, and how does width become depth?

**Key Topics:**
- Ion-enhanced W etching; flux estimates
- Coburn–Winters; slot transmission; linear ARDE and k
- Time to depth (32.4 s); ∂z_r/∂w = 0.87
- Pads (≈ 72 nm) and isolated ends (≈ 57 nm)
- Corner shadowing; weak antenna charging; global loading (Φ = 1.9)

**Prerequisites:** Chapters 1–2; Books #1–5  
**Cross-References:** Appendix B.7, Appendix E.2–E.4  
**Critical Equations:** ER₀t = (h − h₀) + (k/2w)(h² − h₀²); ∂h/∂w; ER(f) = ER(0)/(1 + Φf)  
**Study Questions:** 6 calculations on flux, ARDE, pads, shadowing, loading

---

### Chapter 4: [Tungsten & TiN Etch Chemistry — Fluorine, Chlorine & Selectivity](./chapters/04-w-tin-etch-chemistry.md)
**Estimated Time:** 75 min | **Difficulty:** Advanced | **Reading Level:** Process/Research roles  
**Focus:** Which halogen etches which metal, and how is the balance set?

**Key Topics:**
- Volatility map: WF₆, TiCl₄ volatile; TiF₄, WCl₆ not
- The χ mixing curve; crossover near 0.62
- Slot ratio vs. open-area ratio
- N₂, O₂, Ar additives; oxide selectivity; silicon behind the oxide
- Breakthrough, residues, post-treatment; reference recipe

**Prerequisites:** Chapter 3  
**Cross-References:** Appendix B; *Aluminum Metal Etch* companion  
**Critical Equations:** Δ_TW ≈ (1 − r)R; ∂r/∂χ ≈ 2.3  
**Study Questions:** 5 calculations on volatility, ratio, and selectivity

---

## Part II: Hardware Design (Chapters 5–9)

### Chapter 5: [Inductively Coupled Conductor Chambers for Word-Line Recess](./chapters/05-icp-conductor-chamber.md)
**Estimated Time:** 60 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process roles  
**Focus:** What chamber gives high radical density at low ion energy?

**Key Topics:**
- ICP vs. CCP vs. remote plasma
- Coil, Faraday shield, gas injection, chuck, pumping
- Ion energy from bias power; bias-voltage control
- Residence time; etch products; conductive window deposits
- Materials; throughput (30 WPH); fleet; matching (±1.4 nm)

**Prerequisites:** Chapters 1–4  
**Cross-References:** Books #11–15  
**Critical Equations:** ⟨V_sh⟩ ≈ ηP_bias/I_i; τ = pV/Q; WPH = 3600/t_cycle  
**Study Questions:** 5 calculations on energy, flow, coupling, and throughput

---

### Chapter 6: [Ion Energy, Pulsing & Atomic-Layer Recess](./chapters/06-ion-energy-pulsing-ale.md)
**Estimated Time:** 80 min | **Difficulty:** Advanced | **Reading Level:** Equipment/Research roles  
**Focus:** How much energy, in what distribution, and why does pulsing help?

**Key Topics:**
- Yields of W, TiN, SiO₂ vs. energy; damage depth
- IED at 13.56 MHz; light vs. heavy ions
- Flux-ratio model: k from 0.055 (CW) to 0.035 (pulsed)
- Ion angular distribution; collisionless sheath
- ALE and quasi-ALE landing; throughput cost

**Prerequisites:** Chapters 3–5  
**Cross-References:** Appendix E.3.2, E.9  
**Critical Equations:** s ≈ (√2/3)λ_D(2V/T_e)^¾; β = β_sat R/(1 + R)  
**Study Questions:** 5 calculations on selectivity, sheath, pulsing, ALE

---

### Chapter 7: [Gas Delivery, F/Cl Balance & Multi-Step Recess Recipes](./chapters/07-gas-fcl-balance-steps.md)
**Estimated Time:** 65 min | **Difficulty:** Intermediate | **Reading Level:** Process/Equipment roles  
**Focus:** How is the recipe built, step by step?

**Key Topics:**
- Pressure, flow, residence time as separate knobs
- χ control; gas-line delays and the step-start horn
- BT, ME, TR, PT design; trim mechanics
- Two-step landing variant
- Centre/edge gas split; gas purity

**Prerequisites:** Chapters 4, 6  
**Cross-References:** Appendix D.1–D.2  
**Critical Equations:** t_fill = Vp/Q; t_clear = t_TiN/ER_lat  
**Study Questions:** 5 calculations on pressure, delays, trim, landing, split

---

### Chapter 8: [Wafer Temperature, Electrostatic Chucks & Radial Recess Uniformity](./chapters/08-temperature-esc-radial.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process roles  
**Focus:** Why does temperature move the step more than the depth?

**Key Topics:**
- Arrhenius shares: +0.47 nm/K depth, −0.74 nm/K step
- Heat balance (≈ 48 W), ΔT ≈ 0.85 K, τ ≈ 1.6 s
- Multi-zone chucks; the wafer edge
- 2×2 radial tuning with gas split and edge temperature
- Transients; chuck surface wear

**Prerequisites:** Chapters 4, 7  
**Cross-References:** Appendix E.8, Appendix C.5  
**Critical Equations:** d ln ER/dT = E_a/kT²; ΔT = Q/hA; τ = mc/hA  
**Study Questions:** 5 calculations on coefficients, heat, tuning

---

### Chapter 9: [Chamber Walls, Metal Deposits, Seasoning & Contamination](./chapters/09-walls-metal-contamination.md)
**Estimated Time:** 65 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process roles  
**Focus:** Where does the metal go, and how does it come back?

**Key Topics:**
- 12 mg W and 2 mg TiN per wafer; wall deposits
- Wall loss and depth: 5% → 3 nm
- WAC with NF₃ and BCl₃; season; first-wafer effect
- Window films; edge ring material and wear; edge tilt
- Particles as stubs; metal contamination; maintenance cycle

**Prerequisites:** Chapters 3, 5  
**Cross-References:** Appendix A.7, Appendix C.2, C.7  
**Critical Equations:** n_F = G/(k_p + k_w + k_wafer)  
**Study Questions:** 5 calculations on deposits, wall loss, tilt, particles

---

## Part III: Process Phenomena (Chapters 10–14)

### Chapter 10: [Recess Depth Control & the Gate–Junction Overlap Window](./chapters/10-recess-depth-overlap.md)
**Estimated Time:** 70 min | **Difficulty:** Advanced | **Reading Level:** Process/Integration/Device roles  
**Focus:** Does the window hold, and where should the target be?

**Key Topics:**
- Depth budget: ±3.3 nm raw, ±2.6 nm with feed-forward
- Overlap budget with x_j: ±3.9 / ±3.3 nm in a ±5 nm window
- Odd/even depth walk; array edge; SWD pads
- GIDL, I_on, retention and tWR fails, row hammer, R_SWL vs. depth
- Optimal target ≈ 60.5 nm

**Prerequisites:** Chapters 1–3  
**Cross-References:** Appendix D.5–D.6  
**Critical Equations:** RSS budget; expected cost over a Gaussian depth distribution  
**Study Questions:** 5 calculations on budgets, walk, and target

---

### Chapter 11: [TiN–W Differential Recess — Horns, Pullback & Cap Integrity](./chapters/11-tin-w-differential-recess.md)
**Estimated Time:** 70 min | **Difficulty:** Advanced | **Reading Level:** Process/Integration roles  
**Focus:** Why must the recipe err toward horns?

**Key Topics:**
- The integral step model; pre-trim horn ≈ 4.5 nm
- The TiN top is the gate edge; tip field; TiN veil
- Slits, keyhole voids, WL–BC shorts
- Trim: lateral removal independent of horn height
- Step budget; alternatives; measurement; asymmetry

**Prerequisites:** Chapters 3, 4, 7  
**Cross-References:** Appendix C.3, Appendix D.7, Appendix E.5  
**Critical Equations:** Δ_TW = ∫(1 − r)dh; r(h) = r_open[1 − s_i(1 − c)]  
**Study Questions:** 5 calculations on step, GIDL, trim, fill

---

### Chapter 12: [Fill Seams, Voids & the Conductor Top Surface](./chapters/12-seams-voids-top-surface.md)
**Estimated Time:** 55 min | **Difficulty:** Advanced | **Reading Level:** Process/Research roles  
**Focus:** What happens when the recess reaches the seam?

**Key Topics:**
- Seam structure and why it conducts fluorine
- Penetration length λ ≈ δ/√s; V-notch model
- Resistance, metrology bias, cap fill
- Voids near the target become cavities
- Grains, nucleation-layer grooves; seam-free fill; recipe choices

**Prerequisites:** Chapters 2, 3, 4  
**Cross-References:** Appendix E.2.4  
**Critical Equations:** λ ≈ δ/√s; tan θ = ER_ℓ/ER_v; w_V = 2d_V tan θ  
**Study Questions:** 5 calculations on penetration, notch, voids

---

### Chapter 13: [Gate-Oxide Integrity, Plasma Damage, GIDL & Retention](./chapters/13-oxide-damage-gidl-retention.md)
**Estimated Time:** 75 min | **Difficulty:** Advanced | **Reading Level:** Device/Process/Research roles  
**Focus:** What does the recess do to the oxide next to the junction?

**Key Topics:**
- Exposure time vs. depth; trim and PT dominate at the gate edge
- Wall and shoulder thinning
- F, Cl, H incorporation; VUV shielding by the slot; charging
- Metal on the wall; trim as Ti cleaner
- Single-trap leakage (16 fA); tail cells ≈ 13,000 per die; VRT; reliability

**Prerequisites:** Chapters 1, 3, 6  
**Cross-References:** Book #26 Ch. 13; Appendix E.7  
**Critical Equations:** I = q e_n; N_tail = n_k A_edge N_cells; solid angle ≈ w/πd  
**Study Questions:** 5 calculations on exposure, loss, VUV, tails

---

### Chapter 14: [Advanced Schemes — Dual-Work-Function Gates, New Metals, ALE, 4F² & 3D DRAM](./chapters/14-advanced-wordline-schemes.md)
**Estimated Time:** 75 min | **Difficulty:** Advanced | **Reading Level:** All roles  
**Focus:** How does the conductor etch change at the next nodes?

**Key Topics:**
- DWF word line: window to ≈ +15 nm; metal recess to 75 nm; poly recess; R +16%
- Mo and Ru: resistance, chemistry (MoF₆, RuO₄), no TiN step
- Recess methods compared
- 4F² VCT: metal spacer etch and top-edge recess
- 3D DRAM: lateral recess across tiers

**Prerequisites:** Chapters 1–13  
**Cross-References:** Books #23–25; *Polysilicon Etch* companion  
**Critical Equations:** R′ = ρ/(w_s h_eff); DWF recess times  
**Study Questions:** 5 calculations on DWF, metals, 4F², 3D

---

## Part IV: Production Scale (Chapters 15–16)

### Chapter 15: [Endpoint, Metrology & Advanced Process Control](./chapters/15-endpoint-metrology-apc.md)
**Estimated Time:** 65 min | **Difficulty:** Intermediate | **Reading Level:** Process/Equipment roles  
**Focus:** How is a recess with no endpoint controlled?

**Key Topics:**
- Why emission has no target endpoint; what it monitors
- In-situ reflectometry on scribe targets
- OCD, XRF, STEM, AFM, e-beam; what each misses
- Electrical monitors: R_SWL, GIDL arrays, combs
- Feed-forward, EWMA feedback, virtual metrology, sampling

**Prerequisites:** Chapters 3, 10, 11  
**Cross-References:** Appendix F; Books #11–15 (endpoint)  
**Critical Equations:** t_ME = t_ref + [ΔH₀ − 0.87Δw]/r_end + C; C_{n+1} = C_n − λΔt_n  
**Study Questions:** 5 calculations on endpoint, targets, APC

---

### Chapter 16: [Post-Recess Integration, Yield & Cost of Ownership](./chapters/16-integration-yield-coo.md)
**Estimated Time:** 60 min | **Difficulty:** Intermediate | **Reading Level:** Integration/Management roles  
**Focus:** What uses the recessed conductor, and what is it worth?

**Key Topics:**
- Post-recess clean (no SC-1, no HF); queue time
- Nitride cap fill and how recess shape affects it
- Self-aligned contacts and SWD contacts
- Defect modes and bitmap signatures
- CoO ≈ $9/wafer ≈ 0.23% yield; DWF doubles it

**Prerequisites:** Chapters 1, 10–13  
**Cross-References:** Appendix G  
**Critical Equations:** CoO = Σ costs / wafers; yield value = Δy × wafer value  
**Study Questions:** 5 calculations on clean, cap margin, cost

---

## Appendices

| Appendix | Content |
|----------|---------|
| [A: Material Properties](./appendices/A-material-properties.md) | W, Mo, Ru, TiN, poly; dielectrics; size-dependent resistivity; reference geometry; chamber materials; contamination |
| [B: Chemistry & Reaction Data](./appendices/B-chemistry-reaction-data.md) | Gases, bond energies, volatility, reactions, emission lines, rate data, flux formulas |
| [C: Standard Procedures](./appendices/C-standard-procedures.md) | Depth series, qualification, step audit, matching, radial tuning, feed-forward check, WAC, idle, queue time |
| [D: Process Windows](./appendices/D-process-windows.md) | Reference recipe, sensitivities, lookups for time, width, overlap, budget, trim, pads, DWF |
| [E: Calculations](./appendices/E-recess-geometry-resistance-calculations.md) | Geometry, Monte Carlo slot transmission (with code), recess equation, loading, step, resistance, device, thermal, sheath |
| [F: Endpoint & Metrology](./appendices/F-endpoint-metrology-reference.md) | Signals by step, field clear, metrology methods, test structures, APC parameters, control limits |
| [G: Troubleshooting](./appendices/G-troubleshooting-guide.md) | 15 symptom tables with causes, checks, and actions |
| [Glossary](./GLOSSARY.md) | Terms and symbols with chapter references |

---

## Reading Paths by Role

### Process Engineer (≈ 9 hours)
3 → 4 → 7 → 10 → 11 → 12 → Appendix D, G

### Equipment Engineer (≈ 8 hours)
5 → 6 → 7 → 8 → 9 → 15 → Appendix C, F

### Integration Engineer (≈ 8 hours)
1 → 2 → 10 → 11 → 14 → 16 → Appendix D, E, G

### Device Engineer (≈ 5 hours)
1 → 10 → 13 → 16

### Researcher (≈ 10 hours)
3 → 4 → 6 → 12 → 13 → 14 → Appendix B, E

---

## Cross-Reference Map to Other Books

| Book | Topic | Relevant Chapters |
|------|-------|-------------------|
| Books #1–5 | Plasma Physics Fundamentals | Ch. 3, 5, 6 |
| Books #6–10 | Dielectric & Fluorocarbon Etch | Ch. 4 (oxide selectivity), 16 (SAC) |
| Books #11–15 | Advanced Plasma Engineering | Ch. 5, 6, 7, 15 |
| Book #21 | Shallow Trench Isolation Etch | Ch. 1 |
| Book #22 | Spacer Etchback | Ch. 7 (timed etchback), 14 (metal spacer) |
| Book #24 | 3D NAND Slit Etch | Ch. 14 (lateral metal recess) |
| Books #23, #25 | 3D NAND Staircase, ON Stack | Ch. 14 (3D DRAM) |
| Book #26 | DRAM Isolation Trench Etch | Ch. 1, 10, 13 |
| Companion | DRAM Buried Word-Line Trench Etch | Ch. 1, 2, 12 |
| Companion | Aluminum Metal Etch | Ch. 4 (chlorine metal etch) |
| Companion | Polysilicon Etch | Ch. 14 (DWF poly recess) |
| Companion | Silicon Nitride Etch | Ch. 16 (cap) |

---

## Study Questions Summary

**Total Study Questions:** 81 (5–6 per chapter × 16 chapters)  
**Nature:** Mostly calculation-based  
**Topics:** Retention budget and overlap window, slot geometry and CMP height, fluxes and ARDE, halogen balance and step, sheath and pulsing, gas delays and trim, thermal coefficients and radial tuning, wall loss and particles, depth budgets and target choice, seam penetration, oxide exposure and tail cells, DWF and new metals, APC, cost

Examples:
- Compute the z_r window from x_j and the device limits
- Compute the slot width from the etched opening and the oxide
- Fit ER₀ and k from a depth series
- Show why a 40 nm pad recesses 12 nm deeper than the array
- Compute the pre-trim horn from the slot rate ratio
- Solve the 2×2 radial tuning for gas split and edge temperature
- Compute the depth shift from a 5% change in wall loss
- Estimate the V-notch from the seam width and the rate ratio
- Count tail cells from killer-trap density and gate-edge area
- Compute the feed-forward time correction for a lot
- Compare the module cost with the value of 0.1% yield

---

## How to Use This Index

1. **First time?** Read PREFACE.md, then this INDEX, then Chapter 1.
2. **Focused reading?** Pick your role from the reading paths above.
3. **Reference mode?** Jump to the chapter. Use Appendix G for symptoms and Appendix E for formulas.
4. **Deep dive?** Read Chapters 1–16 in order and work the study questions.

---

**Index Version:** 1.0  
**Last Updated:** 2026-10-04  
**Next:** Begin [Chapter 1: The DRAM Cell Array & the Role of the Buried Word-Line Conductor](./chapters/01-dram-cell-wordline-architecture.md)
