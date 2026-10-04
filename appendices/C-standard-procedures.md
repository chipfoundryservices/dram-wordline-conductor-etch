# Appendix C: Standard Operating Procedures

Procedures for characterizing, qualifying, matching, and maintaining the DRAM word-line recess. Each procedure lists its purpose, the wafers and structures needed, the steps, and the acceptance criteria (illustrative). Adapt sample sizes and limits to the product and fab.

---

## C.1 Depth-Series Characterization (ER₀ and k)

**Purpose:** Extract the open-area rate ER₀ and the ARDE coefficient k of the main step, and the time-to-depth curve for the array, pads, and scribe targets (Chapters 3, 7, 15).

**Wafers:** 6 patterned wafers from one CMP lot, with array, 30 nm and 40 nm pad, and 1 µm test-pad structures; post-CMP OCD on all.

```
Steps:
1. Run BT + ME stopped at 10, 15, 20, 25, 30 s, and the full APC time
   (6 wafers); no TR, no PT (to see the untrimmed step)
2. OCD on array and scribe targets (13 sites); XRF on the W test array
3. STEM cross-sections at centre and edge on the 15 s, 25 s, and full
   wafers: W top, TiN top, notch, wall oxide
4. AFM on 30 nm, 40 nm, and 1 µm pads
5. Fit h(t) for each width simultaneously to
   ER₀ t = (h − h₀) + (k/2w)(h² − h₀²)   (Appendix E.3)
   using the measured h₀ for each structure

Acceptance (reference):
  ER₀ = 180 ± 6 nm/min; k = 0.035 ± 0.004
  Array z_r at the full time = 60.0 ± 1.0 nm; 40 nm pad z_r ≤ 73 nm
  Pre-trim Δ_TW (STEM) = +3 to +6 nm at centre and edge
```

---

## C.2 Chamber Qualification After Wet Clean

**Purpose:** Return a chamber to production after a full wet clean or a major part change (Chapter 9).

```
Steps:
1. Leak check and base pressure; RF (source, bias) and MFC calibration
   verification; bias V_pp at the reference setpoint
2. ESC: He leak per zone with a bare wafer; zone temperature calibration
   with a calibration wafer under plasma load (± 0.5 K)
3. Season: 25 dummy wafers with the full recipe + WAC (walls to steady
   state; WAC-1 endpoint time stable within ± 0.5 s over the last 5)
4. Particle check: 3 bare Si wafers through the full recipe without
   bias in ME (adders ≥ 40 nm)
5. Rate check: 2 blanket W wafers and 2 blanket TiN wafers, ME only, 30 s
6. Product check: 2 product wafers with post-CMP OCD; full recipe;
   post-etch OCD (13 sites), XRF, 1 STEM site at the edge

Acceptance (illustrative):
  Particles: ≤ 5 adders ≥ 40 nm per wafer
  Blanket W rate within ± 3% of the fleet mean; TiN rate within ± 4%;
    ratio r within ± 0.02 of the fleet mean
  Product z_r within ± 1.0 nm of target after the post-clean C_chamber;
    radial range ≤ 3 nm; Δ_TW after trim within −1.5 to +1.0 nm
  F/Ar actinometry within ± 3% of the chamber's pre-clean baseline
```

---

## C.3 TiN–W Step Audit

**Purpose:** Confirm that the trim removes horns and that no slits form (Chapter 11).

```
Frequency: weekly per chamber; after any TiN or W deposition change; after
a trim-rate excursion

Steps:
1. Select one production wafer per chamber (random slot)
2. STEM + EDX cross-sections across 5 word lines at centre, mid-radius,
   and edge (3 mm from the edge) → 15 slots, 30 walls
3. For each wall: TiN top relative to W top (Δ_TW); veil above z = 0;
   slit depth; horn asymmetry between walls of the same slot
4. Record notch depth and wall oxide thickness at z = 10 and 55 nm

Acceptance:
  All walls: −2.0 ≤ Δ_TW ≤ +2.0 nm; no TiN above z = 40 nm; no slit
    deeper than 2 nm with re-entrant shape
  Edge asymmetry (left − right horn) ≤ 1.0 nm
  Notch ≤ 8 nm; wall oxide ≥ 3.2 nm at z = 10 nm
```

---

## C.4 Chamber Matching

**Purpose:** Hold chamber-to-chamber differences within the matching budget (Chapter 5.7.3).

```
Steps:
1. Run one matching lot of 2 product wafers per chamber from one CMP lot
   on the same day, with APC feed-forward on and C_chamber frozen
2. Post-etch OCD (13 sites), XRF, and 1 STEM audit site per chamber
3. Compute each chamber's mean z_r offset from the fleet mean, its radial
   signature, and its Δ_TW
4. Update C_chamber; if the radial signature differs from the fleet by
   > 1.5 nm (edge − centre), retune gas split and edge zone (Ch. 8.4)

Acceptance:
  Residual chamber offset after C_chamber update ≤ ± 0.7 nm (3σ, fleet)
  Δ_TW mean within ± 0.7 nm of the fleet mean
```

---

## C.5 Radial Tuning (Gas Split and Edge Zone)

**Purpose:** Flatten the radial depth and step profiles together (Chapters 7.5, 8.4).

```
Steps:
1. Run 4 product wafers: baseline; centre fraction +10%; edge zone +2 K;
   both changes
2. OCD radial profile (≥ 17 sites incl. r = 145 mm); STEM at centre and
   edge for Δ_TW (untrimmed sister wafers, or pre-trim from C.1)
3. Fit the 2×2 sensitivity matrix:
   [∂D/∂g  ∂D/∂T_e]
   [∂S/∂g  ∂S/∂T_e]     D, S: edge − centre depth and step
4. Solve for Δg, ΔT_e that bring D and S to zero; limit |Δg| ≤ 15%,
   |ΔT_e| ≤ 5 K
5. Verify with 2 wafers

Acceptance: |D| ≤ 1.0 nm; |S| ≤ 0.8 nm (pre-trim)
```

---

## C.6 Feed-Forward Model Check

**Purpose:** Confirm the APC coefficients for starting height and CD (Chapter 15.5).

```
Steps:
1. Select 3 lots with a natural spread in post-CMP height (≥ 2 nm range)
   and WL CD (≥ 1 nm range)
2. Run with APC feed-forward off (fixed time)
3. Regress post-etch z_r against Δh_start and Δw:
   z_r = z₀ − a Δh_start + b Δw
4. Expected: a ≈ 1.0 (each nm of starting height is a nm of depth error),
   b ≈ 0.87

Acceptance: a = 1.0 ± 0.15; b = 0.87 ± 0.2; residual 3σ ≤ 2.0 nm
```

---

## C.7 Per-Wafer WAC and Season Verification

**Purpose:** Confirm that the waferless autoclean removes W and Ti deposits and that the season restores the wall (Chapter 9.3).

```
Steps:
1. Trend WAC-1 endpoint time (F 703.7 nm plateau) per wafer
2. Trend Ti 498–500 nm emission at the end of WAC-2
3. Monthly: coupon on the liner (if fitted) → XPS for Ti, W, S

Acceptance:
  WAC-1 endpoint time stable within ± 15% over a wet-clean cycle
  Ti emission at the end of WAC-2 ≤ 1.1 × the post-wet-clean value
  Coupon: no Ti fluoride growth > 5 nm per 500 RF hours
```

---

## C.8 Idle Recovery

**Purpose:** Remove the first-wafer effect after idle (Chapters 8.5.2, 9.2.3).

```
Trigger: chamber idle ≥ 30 min
Steps: WAC (full) + 60 s waferless season (ME chemistry, 700 W) + 1 dummy
       wafer with the full recipe if idle ≥ 4 h
Acceptance: first product wafer z_r within ± 0.8 nm of the lot mean
            (checked by virtual metrology; OCD on the first wafer weekly)
```

---

## C.9 Post-Recess Queue-Time Control

**Purpose:** Limit W oxidation and halogen residue before the clean and cap (Chapter 16.1.3).

```
Limits: recess → clean ≤ 2 h; clean → cap ≤ 4 h
Excursion: if recess → cap > 24 h:
  1. XPS or ellipsometry on a monitor wafer from the same lot (WOₓ)
  2. If WOₓ > 1.5 nm or haze visible: re-clean with the standard clean
     (one time only; W loss ≤ 0.3 nm) and cap within 2 h
  3. Flag the lot for WL-pad contact resistance review at parametric test
```

---

**Appendix C Version:** 1.0
