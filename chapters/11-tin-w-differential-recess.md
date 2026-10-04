# Chapter 11: TiN–W Differential Recess — Horns, Pullback & Cap Integrity

## Overview

The recess front in each slot has three strips: TiN on the left wall, tungsten in the middle, and TiN on the right wall. If they move down together, the conductor top is flat and the nitride cap fills a simple rectangle above it. If the TiN lags, it is left standing above the tungsten as a thin wall, called a **horn**. If the TiN leads, it is pulled down below the tungsten and leaves a narrow **slit** between the tungsten and the oxide. Each shape has its own failure mode, and both change the one thing that matters most for the transistor. The TiN lies against the gate oxide, so **the TiN top is the gate edge**. The tungsten top, 2 nm farther from the oxide, is not.

This chapter explains how the TiN–W step forms and grows with depth, what horns and slits do to the gate edge, the cap, and the contacts, how the trim step works and where it fails, and how the step is measured and budgeted.

**Learning Objectives:**
- Model the TiN–W step as an integral of the slot rate ratio over the recess
- Explain why the TiN top, not the tungsten top, sets the gate edge
- Predict the effect of a horn on GIDL, cap thickness, and contact margin
- Predict the effect of a slit on cap fill, voids, and word-line-to-contact shorts
- Design a trim and show why it tolerates horns but not pullback
- Build a step budget and choose the pre-trim horn target

---

## 11.1 How the Step Forms

### 11.1.1 The Integral Model

If both metals recess only from the top, the step after a recess of depth R is the integral of the rate mismatch:

```
Δ_TW = ∫₀^R [1 − r(h)] dh      r(h) = ER_TiN(h) / ER_W(h) in the slot

Δ_TW > 0: TiN above W (horn)
Δ_TW < 0: TiN below W (pullback, slit)
```

### 11.1.2 The Slot Ratio

The open-area ratio of the reference main step is r_open = 0.97 (Chapter 4.4). In the slot, part of the TiN rate depends on ions, and the corners where the TiN sits are shadowed (Chapter 3.5.2):

```
r(h) = r_open × [1 − s_i (1 − c(h))]

s_i:   ion-assisted share of the TiN rate (reference ME: ≈ 0.12)
c(h):  ion flux at the corner relative to the slot centre;
       ≈ 1.0 at h = 0, falling to ≈ 0.6 at h = 88 nm (take linear)

Average c over the recess ≈ 0.80
  r_avg = 0.97 × [1 − 0.12 × 0.20] = 0.97 × 0.976 = 0.947
  Δ_TW = (1 − 0.947) × 85 ≈ +4.5 nm before trim
```

The reference main step therefore leaves a horn of about 4.5 nm. About half of it comes from the open-area rate mismatch, which is deliberate (Section 11.4), and half from corner shadowing.

### 11.1.3 What Moves the Step

```
Change                              Effect on pre-trim Δ_TW (illustrative)
──────────────────────────────────────────────────────────────────────────────
χ +0.01 (more Cl)                   −2.0 nm
TiN oxygen +4 at.% (Ch. 2.2.2)      +9.7 nm (TiN rate −12%)
Wafer +1 K (Ch. 8.1.2)              −0.74 nm
Pressure 8 → 12 mTorr (Ch. 7.1.1)   +1.0 nm
Bias +10 V                          −0.4 nm (more TiN sputter)
Oxygen-rich walls after clean       +1 to +2 nm (first wafer)
(Ch. 9.2.3)
SF₆-first gas transient             +2.5 nm (Ch. 7.2.2)
(0.7 s)
```

The largest single risk is the TiN film itself. A TiN deposition change that adds a few percent of oxygen changes the step more than any etch knob. The recess module must monitor incoming TiN composition, or at least the TiN sheet resistance as a proxy, and the trim must tolerate the resulting horn range.

---

## 11.2 Horns

### 11.2.1 The Gate Edge Is the TiN Top

```
Cross-section of one slot wall with a horn (not to scale):

   oxide │TiN│        │
   wall  │ ▓ │        │   ← horn: TiN 2 nm thick, Δ_TW tall
         │ ▓ │        │
         │ ▓ │████████│ ← W top (z_W)
    Si   │ ▓ │████████│
         │ ▓ │████████│
       3.5 nm 2 nm

Gate edge facing the silicon = TiN top = z_W − Δ_TW
```

The silicon on the other side of the gate oxide sees the TiN. A horn raises the gate edge by Δ_TW, even if the tungsten top is exactly on target:

```
W top at 60 nm, horn Δ_TW = +3 nm → effective gate edge at 57 nm
  Overlap Δ_ov = 62 − 57 = +5 nm (instead of +2)
  GIDL ≈ 10^(3/8) ≈ 2.4× the target value
```

The thin horn also concentrates the field at its tip. A 2 nm wide conductor with a rounded tip of about 1 nm radius gives a local field at the oxide a few tens of percent higher than a flat gate edge at the same height. GIDL depends exponentially on field, so the horn's real effect is larger than the overlap calculation alone suggests.

### 11.2.2 Horns and the Cap

The nitride cap covers the horn. Over the horn tip, the cap is thinner by Δ_TW:

```
Cap thickness above the conductor (reference): from z = 60 nm to the cap
CMP plane at z ≈ −20 nm → ≈ 80 nm over W; ≈ 77 nm over a 3 nm horn
```

The thickness is rarely the problem. The position is. The horn runs along the slot wall, directly under the edge of the cap. The storage-node contact (BC) lands on the silicon beside the word line, and its etch, if misaligned, cuts into the cap shoulder. The horn is the first metal it meets. A horn shortens the BC-to-word-line distance along exactly the path the misaligned contact etch takes.

### 11.2.3 The TiN Veil

The worst form of horn is the one left on the walls above the silicon surface. If the main step leaves TiN on the hard-mask walls above z = 0 and the trim does not clear it, a continuous TiN film runs from the conductor up to or past the silicon surface:

```
TiN veil (failed trim):

  mask │ ▓ │        │ ← TiN left on mask wall
 ──────┤ ▓ ├────────┤── Si surface
   Si  │ ▓ │        │ ← TiN on gate oxide: gate edge now at the Si surface
       │ ▓ │████████│ ← W top at 60 nm
```

The gate then overlaps the entire junction. The cell leaks heavily, and in the worst case the veil links to the contact. A veil usually comes from TiN that was not broken through at the start (oxidized TiN top after a long CMP queue, Chapter 4.7) and then lagged all the way down. It is caught by STEM/EDX audits and by GIDL test structures (Chapter 15).

---

## 11.3 Pullback and Slits

### 11.3.1 How a Slit Forms

If the TiN etches faster than tungsten in the slot (r > 1), the TiN top falls below the tungsten top and leaves a slit 2 nm wide between the tungsten and the oxide wall:

```
Slit (pullback), Δ_TW < 0:

   oxide │   │        │
   wall  │ ░ │████████│ ← W top
         │ ░ │████████│   ░ slit: 2 nm wide, |Δ_TW| deep
         │▓▓▓│████████│ ← TiN top
    Si   │▓▓▓│████████│
```

Once the slit exists, it etches like a very high aspect-ratio feature. A slit 2 nm wide and 3 nm deep has an aspect ratio of 1.5, and the ARDE of Chapter 3 slows its deepening. That is why pullback in the main step is often self-limiting at a few nanometres. The trim, though, uses chlorine, which etches TiN chemically, and deepens the slit more readily.

### 11.3.2 The Slit and the Gate Edge

With TiN pulled back, the conductor facing the oxide at the top is tungsten across a 2 nm gap filled later with nitride. The tungsten top still couples to the channel, but through 2 nm of nitride in series with 3.5 nm of oxide. Its control is weaker, so the effective gate edge lies between the TiN top and the tungsten top. Pullback therefore acts like a small over-recess at the wall: it reduces GIDL and adds underlap resistance.

### 11.3.3 The Slit and the Cap

The real danger is the cap. The nitride cap is deposited by ALD (a liner) and then CVD (the bulk fill). A 2 nm slit can be filled by ALD only if it is not re-entrant:

```
Slit fill outcomes:

Slit shape                     ALD liner           Result
──────────────────────────────────────────────────────────────────────────
Open V (W top corner rounded)  Fills from bottom   Solid; no void
Straight, 2 nm, ≤ 3 nm deep    Fills (1 nm/side)   Solid if ALD ≥ 1.2 nm
Re-entrant (W top overhangs,   Pinches at top      Keyhole void along the
  deeper than ≈ 3 nm)                              word line
```

A keyhole void runs along the word line, beside the wall, under the cap. It is invisible until the BC contact etch and its clean reach it. An HF-containing clean then widens it, and the contact metal (polysilicon or TiN/W) flows into it and touches the word-line tungsten. The result is a **word-line-to-storage-node short**, a hard failure that often affects every cell along a stretch of word line.

### 11.3.4 Why Pullback Is Worse Than a Horn

```
Comparison at |Δ_TW| = 3 nm (illustrative):

                      Horn (+3 nm)                Slit (−3 nm)
─────────────────────────────────────────────────────────────────────────
Gate edge             Higher by 3 nm: GIDL ×2.4   Lower and weaker at the
                      plus tip field              wall: small I_on loss
Cap                   Slightly thinner at wall    Keyhole void risk
Contacts              Shorter BC path             WL–BC short through void
Fixable by trim?      Yes (lateral removal)       No (trim deepens the slit)
Failure type          Parametric (retention)      Hard (shorts)
```

A horn can be removed by the next step, and if it is not, it causes a parametric loss. A slit cannot be removed and causes hard failures. **The recipe is therefore designed to err toward horns and then remove them.**

---

## 11.4 The Trim

### 11.4.1 How the Trim Works

The trim (Chapter 7.3.3) runs at high pressure, very low bias, and chlorine with a little oxygen. Its ions arrive at wide angles with little energy. It etches TiN chemically and tungsten very slowly. A horn has its inner face fully exposed to the slot, so the trim attacks it from the side along its whole height:

```
Horn removal time ≈ t_TiN / ER_lateral = 2.0 nm / 0.6 nm/s ≈ 3.3 s

Independent of horn height, as long as the inner face is exposed
```

### 11.4.2 Trim Outcome Versus Pre-Trim Step

```
Reference trim: 6 s; TiN lateral 0.6 nm/s; TiN in slit 0.3 nm/s;
W 0.15 nm/s (illustrative)

Pre-trim Δ_TW     Horn cleared at     Post-trim Δ_TW     W top lowered
─────────────────────────────────────────────────────────────────────────
+9 nm             3.3 s               −0.4 nm            0.9 nm
+4.5 nm           3.3 s               −0.4 nm            0.9 nm
+2 nm             3.3 s               −0.4 nm            0.9 nm
+0.5 nm           ≈ 1 s (thin, short) −1.1 nm            0.9 nm
−2 nm (slit)      —                   −2.9 nm            0.9 nm
```

The trim gives nearly the same result for any horn from 2 to 9 nm. Below about 1 nm of horn, it starts to over-trim, and with a pre-existing slit it makes things worse. This sets the design rule:

```
Pre-trim horn target ≥ 3σ of the pre-trim step distribution + 1 nm

Pre-trim step budget (3σ, illustrative):
  TiN composition (incoming, monitored)   ±1.0 nm
  Temperature (radial, after tuning)      ±0.6 nm
  χ and MFC                               ±0.5 nm
  Wall state                              ±0.6 nm
  Corner shadowing (slot width, depth)    ±0.5 nm
  RSS                                     ±1.5 nm

  Target ≥ 1.5 + 1.0 = 2.5 nm; reference target 4.5 nm (margin for
  a TiN excursion)
```

### 11.4.3 What the Trim Costs

```
Cost of the trim                         Size
──────────────────────────────────────────────────────────────────────
W lowered (counted in the ME target)     ≈ 0.9 nm
Gate-oxide exposure at low energy        Negligible loss; adds Cl
Throughput                               6 s + 1 s ramp
Mask loss                                ≈ 0.1 nm
```

The trim is cheap. Its main risk is a chamber change that slows the lateral TiN rate (a wall or temperature change), which leaves the tallest horns partly in place. That shows as a growing tail of post-trim horns in STEM audits, not as a mean shift.

---

## 11.5 Alternatives to Main-Step-Plus-Trim

```
Strategy                       How it works                      Weakness
──────────────────────────────────────────────────────────────────────────────────────
Rate-matched single step       χ at the slot crossover; no trim  Needs r within ±3.5%
                                                                 everywhere, always
W-fast ME + lateral trim       Reference (this chapter)          Trim rate drift
(reference)
TiN-fast ME + W catch-up       Ends with TiN pulled back, then   Isotropic W step opens
                               an F-only, no-bias W step         the seam (Ch. 12)
Alternating ME/TR cycles       Short ME and TR steps repeated;   More transitions; more
                               horn never exceeds ≈ 1–2 nm       time
Dry W recess + wet TiN recess  Plasma for W; peroxide-based wet  Wet attacks W too;
                               chemistry for TiN                 needs a selective
                                                                 formulation; queue
ALE landing                    Saturating half-cycles etch both  Time (Ch. 6.5)
                               metals per cycle
```

Alternating short main and trim steps keeps horns small throughout, so corner shadowing never grows. It is useful where the slot is narrower and the corner effect is larger, at the cost of more transitions and a few seconds.

---

## 11.6 Measuring the Step

```
Method                    What it sees                     Use
──────────────────────────────────────────────────────────────────────────
STEM + EDX/EELS mapping   Ti and W tops separately;        Reference; audits;
(cross-section)           horns, slits, veils              development
OCD scatterometry         Composite metal top; TiN         In-line; weak on
                          parameter weakly separable       2 nm TiN
                          (2 nm of a 11 nm slot)
GIDL test structures      Effective gate edge (electrical) End of line; most
(after full flow)                                          direct
Cap void inspection       Voids after cap (e-beam voltage  After cap; WL–BC
(e-beam, TEM)             contrast, plan-view TEM)         short risk
```

The effective gate edge cannot be measured in line with confidence. The step is controlled by keeping the trim robust and by auditing STEM cross-sections at a regular frequency, with GIDL test structures as the final check (Chapter 15).

---

## 11.7 Asymmetric Steps

A slot can have a horn on one wall and none on the other. Causes:

```
Cause                                  Signature
──────────────────────────────────────────────────────────────────────────
Ion tilt at the wafer edge (ring       Outer 2–5 mm; horn on the wall facing
wear, Ch. 9.5.2)                       the wafer centre
Asymmetric slot (word-line trench      Throughout the wafer; correlates with
profile; overlay to the AA)            trench sidewall angle difference
Local charging (one wall over an AA,   Pattern-dependent; reduced by pulsing
the other over isolation)
```

An asymmetric horn survives a trim only if it is unusually thick or the trim is weak. Its main importance is diagnostic: it points to ion direction rather than chemistry.

---

## 11.8 Summary & Key Takeaways

1. **The step is the integral of the slot rate mismatch.** With r_open = 0.97 and corner shadowing, the reference main step leaves a 4.5 nm horn.

2. **The TiN top is the gate edge.** A 3 nm horn raises the gate edge 3 nm and raises GIDL about 2.4×, plus a tip-field penalty, even with the tungsten on target.

3. **A slit is worse than a horn.** Pullback leaves a 2 nm slit that can close into a keyhole void in the cap. The BC contact finds it later as a hard short.

4. **The trim removes horns from the side.** A 2 nm horn clears in about 3.3 s regardless of its height. The trim cannot fix a slit and deepens it.

5. **Design to err toward horns.** The pre-trim horn target must exceed the 3σ step variation plus margin. The reference uses 4.5 nm.

6. **TiN composition is the biggest risk.** A few percent of extra oxygen in the TiN changes the step more than any etch knob.

---

## Study Questions

1. With r_open = 0.99, s_i = 0.20, and c(h) falling linearly from 1.0 to 0.5 over the recess, compute the pre-trim step for R = 85 nm. Is a 6 s reference trim sufficient?

2. A horn of 2.5 nm remains after a weak trim on the edge dies. Compute the overlap and the GIDL ratio from the flat-edge model. If the tip field adds 15% to the field and GIDL rises by a factor of 1.8 for that field increase, what is the total GIDL ratio?

3. The trim's TiN slit rate is 0.3 nm/s and W rate 0.15 nm/s. For a pre-trim step of +1.0 nm, compute the time to clear the horn (lateral rate 0.6 nm/s, but the horn is only 1 nm tall and partly shielded) and the post-trim step for a 6 s trim. Would you shorten the trim?

4. An ALD SiN liner of 1.0 nm per side is deposited on a slit 2.0 nm wide whose top is narrowed to 1.6 nm by a W overhang. Will it pinch off? What is the minimum overhang that creates a void?

5. A new TiN precursor lowers the film oxygen from 5% to 2% and raises the TiN rate by 9%. Compute the new pre-trim step. Is the reference design still erring toward horns? What χ change would restore a 4.5 nm horn?

---

**Next Chapter:** [Chapter 12: Fill Seams, Voids & the Conductor Top Surface](./12-seams-voids-top-surface.md)

---

**Chapter 11 Development Status:** Complete  
**Version:** 1.0
