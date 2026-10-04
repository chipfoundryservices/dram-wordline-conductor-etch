# Chapter 15: Endpoint, Metrology & Advanced Process Control

## Overview

The word-line recess has no endpoint at its target. The exposed metal area is the same at the start and at the end, so the plasma emission does not change when the surface passes 60 nm. The recess is controlled the way Book #26 controls a trench that ends in bulk silicon: by time, set from what is known before the etch and corrected by what is measured after it. What is known before is the post-CMP height and the word-line CD. What is measured after is the conductor depth by scatterometry, the amount of tungsten left by X-ray fluorescence, the shape by cross-section microscopy, and, weeks later, the electrical behavior of word-line and GIDL test structures.

This chapter covers what optical emission can and cannot tell the recess, in-situ reflectometry on dedicated targets, the in-line and off-line metrology of the recessed conductor, electrical monitors, and the feed-forward and feedback control that sets the main-step time for each wafer.

**Learning Objectives:**
- Explain why optical emission gives no endpoint at the target, and what it does provide
- Use in-situ spectral reflectometry on a scribe target and know its limits
- Choose among OCD, XRF, STEM, and AFM for depth, step, and shape
- Use electrical test structures to measure the effective gate edge and word-line height
- Compute a feed-forward time correction from incoming height and CD
- Run an EWMA feedback loop with chamber and product constants

---

## 15.1 Optical Emission

### 15.1.1 Why There Is No Endpoint

```
Exposed metal area during the recess:   constant (the slot tops)
Exposed oxide area:                     constant (mask top), plus walls that
                                        grow but are shadowed
Etch products (WF₆, TiCl₄):             constant, falling slightly with ARDE

At the target depth, nothing changes in the plasma.
```

### 15.1.2 What Emission Does Show

```
Signal                       What it tracks                       Use
──────────────────────────────────────────────────────────────────────────────────
F 703.7 nm / Ar 750.4 nm     Free F density (actinometry):        Loading and wall-state
  (actinometry)              falls with metal area and wall loss  drift; rate predictor
Cl 837.6 nm / Ar             Free Cl density                      χ verification
W lines (e.g. 400.9 nm),     W-containing species in the gas      Etch-product level;
  WF band                                                         rate proxy
Ti lines (e.g. 498–500 nm)   Ti species                           TiN etch activity;
                                                                  WAC endpoint
Breakthrough transient       Rise of W emission as the WOₓ        BT completion check
                             skin clears (first 2–4 s)
F rise at field clear        Etchback-only flow: metal area       True endpoint for the
                             collapses when the field clears      field-clear step
```

In an etchback-only flow (Chapter 2.5), the field clear is a real endpoint: the metal area falls by a factor of about six, and the fluorine emission rises sharply. In the reference CMP-then-recess flow, emission is a **monitor of rate**, not an endpoint. A 3% drop in F/Ar actinometry during the main step, at fixed recipe, predicts a slower etch and a shallower recess before any wafer is measured.

---

## 15.2 In-Situ Reflectometry

### 15.2.1 The Principle

A broadband light beam through a window above the wafer reflects from a dedicated grating target. The target has metal-filled slots, like the array, with a pitch large enough for a clean optical model. As the metal top descends, the phase difference between light reflected from the metal top and from the mask top changes, and the reflected spectrum shifts:

```
Phase change for a recess Δh at wavelength λ (normal incidence):
  Δφ = 4π Δh / λ

At λ = 400 nm, 85 nm of recess: Δφ = 4π × 85/400 = 2.67 rad (0.42 fringe)
```

Less than half a fringe over the whole recess is too little for fringe counting. Model-based fitting of the full spectrum (250–800 nm) tracks the depth continuously to about ±1 nm on a well-designed target.

### 15.2.2 Limits

```
Limit                                      Consequence
──────────────────────────────────────────────────────────────────────────
Target must be in the scribe line or a     Its CMP height and its ARDE differ
  dedicated in-die area                    from the array (Ch. 3.4)
Target slots must be wider than the        Wider slots recess faster; the target
  array's for a usable optical model       depth must be translated with the
                                           ARDE model
Window clouding by deposits                Signal loss over a wet-clean cycle
One target per wafer (centre)              No radial information
```

In-situ reflectometry is therefore used to **stop on a predicted target depth**: the APC computes what the scribe target's depth should be when the array reaches 60 nm, and the etch stops when the target reaches that value. This removes wafer-to-wafer rate variation (chamber drift, wall state) from the budget. It does not remove within-wafer or array-versus-target differences.

---

## 15.3 Post-Etch Metrology

### 15.3.1 Methods

```
Method               Measures                              Accuracy / note
──────────────────────────────────────────────────────────────────────────────────────
OCD (scatterometry)  Average metal-top depth in the array  ±0.7 nm vs. TEM (in-die
on in-die targets    or a grating; mask thickness; slot    targets); TiN top weakly
                     width; weak sensitivity to TiN top    separable; notch biases
                                                           depth (Ch. 12.3.2)
XRF                  W areal mass on a test array →        ±1% of W remaining ≈
                     average conductor height              ±1 nm; insensitive to
                                                           shape; robust
HAADF-STEM + EDX     W top, TiN top, notch, horn, oxide    Sub-nm; destructive;
(cross-section)      thickness, residue                    few sites per week
AFM                  Pad recess (≥ 30 nm pads); dishing    ±0.5 nm on pads; cannot
                     before etch                           enter 11 nm slots
CD-SEM               Top width of the slot (mask CD);      No depth
                     particles, stubs
E-beam inspection    Unrecessed stubs (charging contrast); After cap: voids, shorts
(voltage contrast)   after cap, opens and shorts           at the WL level
```

### 15.3.2 What Each Method Misses

```
Defect                      OCD        XRF        STEM          AFM     E-beam
────────────────────────────────────────────────────────────────────────────────
Depth shift (mean)          Yes        Yes        Yes (few)     Pads    No
TiN horn / slit             Weak       No         Yes           No      No
V-notch                     Biased     No         Yes           No      No
Particle stub               No         No         Unlikely      No      Yes
Cap void (later)            No         No         Yes (if hit)  No      Yes
Oxide thinning              Weak       No         Yes           No      No
```

No in-line method sees the TiN–W step reliably. The step is controlled by keeping the trim robust and auditing it by STEM (Chapter 11.6).

---

## 15.4 Electrical Monitors

```
Test structure                    Measures                            Detects
──────────────────────────────────────────────────────────────────────────────────────
Word-line resistance line         R per µm → effective conductor       Over-recess,
(sub-WL length, pads at both      height; R/R_ref ≈ 108/(h_eff)        punch-through,
ends)                                                                  cavities
GIDL array (cell transistors      Drain leakage vs. V_G, V_D, T;       Overlap (incl. horns),
with accessible SN node)          BTBT vs. TAT from T dependence       damage
Cell I_on array                   Drive current                        Underlap
WL–BC comb (WL lines interleaved  Leakage/short between WL and          Slits, stubs, horns +
with BC contacts)                 contacts                             misalignment
WL–WL comb                        Short between adjacent WLs           CMP residue; 4F²
                                                                       spacer bridges
Capacitance WL–BC                 Cap thickness at the wall            Horns, pullback
Retention bitmap (wafer sort)     Tail count, VRT                      Overlap + damage
```

The GIDL array is the only measurement of the **effective gate edge**, the combined result of the W top, the TiN top, the horn tip, and the junction. Its temperature dependence separates band-to-band tunnelling (weak T dependence, set by overlap) from trap-assisted tunnelling (stronger T dependence, set by damage).

---

## 15.5 Advanced Process Control

### 15.5.1 The Time Model

```
t_ME = t_ref + [Δh_start − (∂z_r/∂w) Δw + Δz_target] / r_end + C_chamber + C_product

Δh_start:      measured array metal-top height above Si, minus the reference
               25 nm (positive = starts higher → needs more recess)
Δw:            measured WL trench CD minus 18.0 nm (positive = wider slot →
               recesses deeper → needs less time)
∂z_r/∂w:       0.87 nm/nm
Δz_target:     target change (if any)
r_end:         2.34 nm/s (rate at the end of the main step)
C_chamber:     chamber constant (s), from feedback
C_product:     product constant (s), from metal area fraction (Ch. 3.7.4)
```

### 15.5.2 Feed-Forward Example

```
Incoming wafer (lot average of 9 OCD sites):
  Array metal top 26.6 nm above Si (reference 25.0) → Δh_start = +1.6 nm
  WL trench CD 18.5 nm → Δw = +0.5 nm

  Correction = [1.6 − 0.87 × 0.5] / 2.34 = (1.6 − 0.44) / 2.34 = +0.50 s
  t_ME = 31.7 + 0.50 + C_chamber + C_product
```

### 15.5.3 Feedback

The chamber constant is updated from post-etch OCD with an exponentially weighted moving average:

```
Error on run n:  e_n = z_r,measured − z_r,target   (nm; + = too deep)
Time error:      Δt_n = e_n / r_end

C_chamber,n+1 = C_chamber,n − λ Δt_n,   λ = 0.3

Example: three lots measure 60.9, 60.7, 60.4 nm (target 60.0)
  Lot 1: Δt = 0.9/2.34 = 0.385 s → C = 0 − 0.3 × 0.385 = −0.115 s
  Lot 2: Δt = 0.7/2.34 = 0.299 s → C = −0.115 − 0.090 = −0.205 s
  Lot 3: Δt = 0.4/2.34 = 0.171 s → C = −0.205 − 0.051 = −0.256 s
```

### 15.5.4 Resets and Constants

```
Event                        APC action
──────────────────────────────────────────────────────────────────────────
Wet clean                    Reset C_chamber to the post-clean qualification
                             value; tighter sampling for 3 lots
Edge-ring replacement        Edge-zone offset re-qualified; C unchanged
New product                  C_product from metal area fraction; first lot
                             measured at full sampling
TiN or W deposition change   Hold; STEM audit of step before release
CMP pad or slurry change     Feed-forward model check (Δh_start coefficient)
```

### 15.5.5 Virtual Metrology

Fault-detection signals that correlate with depth can be used as a per-wafer feed-forward between OCD measurements:

```
Signal (per wafer)                 Correlation with z_r (illustrative)
──────────────────────────────────────────────────────────────────────────
F/Ar actinometry in ME (mean)      +0.8 nm per +1% (more F → faster →
                                   deeper)
WAC endpoint time                  −0.3 nm per +1 s (more wall deposit →
                                   walls consume more F → shallower)
Bias V_pp in ME                    +0.2 nm per +1 V
He leak (zone)                     Radial step and depth (Ch. 8.6)
Reflectometry target depth         Direct (Section 15.2)
```

A model fitted on these signals predicts the depth of every wafer, not only the sampled ones, and flags wafers for measurement when the prediction moves outside a guard band.

---

## 15.6 Sampling Plan

```
Measurement                 Sampling (illustrative)          Purpose
──────────────────────────────────────────────────────────────────────────────
Post-CMP OCD (array height)  Every wafer, 9 sites              Feed-forward
WL trench CD                 Every lot, 2 wafers × 9 sites    Feed-forward
Post-recess OCD              Every lot, 2 wafers × 13 sites   Feedback, radial
                             (incl. edge)
XRF (W remaining)            Every lot, 1 wafer               Cross-check of OCD
STEM audit (horn, notch,     Weekly per chamber, 3 sites      Step and shape
  oxide)
E-beam stub inspection       Every lot, 1 wafer, sampled area Particles → stubs
WL R, GIDL, combs            Every wafer at parametric test   Electrical truth
Retention bitmap             Every wafer at sort              Tail and VRT
```

---

## 15.7 Summary & Key Takeaways

1. **There is no endpoint at the target.** The exposed metal area does not change. Emission monitors rate and wall state, and gives a true endpoint only for field clear in an etchback-only flow.

2. **Reflectometry can stop on a predicted depth.** A scribe grating target tracks depth continuously, which removes wafer-to-wafer rate drift, but its depth must be translated to the array with the ARDE model.

3. **No in-line tool sees the TiN–W step well.** OCD and XRF measure the average depth. STEM audits and GIDL arrays check the step and the effective gate edge.

4. **Electrical monitors are the ground truth.** Word-line resistance gives effective height, GIDL arrays give the effective gate edge, and comb structures catch slits and stubs.

5. **Feed-forward handles the incoming height and CD.** Each nanometre of starting height costs 0.43 s of etch, and each nanometre of CD saves 0.37 s.

6. **Feedback and virtual metrology handle the chamber.** An EWMA chamber constant with resets at wet clean, plus per-wafer prediction from FDC signals, keep z_r on target between measurements.

---

## Study Questions

1. In an etchback-only flow, the field clears when 60 nm of W has been removed from a surface with 100% metal coverage, and the metal fraction then drops to 0.16. Using the loading model with Φ = 1.9, compute the factor by which the F density rises at field clear. Is this a usable endpoint signal?

2. A scribe target has 30 nm slots with h₀ = 6 nm and a mask top at 29 nm. What target depth should the reflectometer stop on so that the array reaches z_r = 60 nm (use the ARDE model of Chapter 3)?

3. An incoming lot has a metal top 23.8 nm above Si and a WL CD of 17.6 nm. Compute the feed-forward time correction.

4. Run the EWMA feedback for four lots measuring 59.2, 59.5, 59.9, and 60.1 nm, starting from C = 0 with λ = 0.3 and λ = 0.6. Which λ settles faster, and what is the risk of the larger one?

5. OCD reports a stable depth, but the WL resistance rises 3% over two weeks and the GIDL arrays are unchanged. Which shape change from Chapter 12 explains this, and which measurement in Section 15.3 would confirm it?

---

**Next Chapter:** [Chapter 16: Post-Recess Integration, Yield & Cost of Ownership](./16-integration-yield-coo.md)

---

**Chapter 15 Development Status:** Complete  
**Version:** 1.0
