# Appendix G: Troubleshooting Guide

Symptom-driven guide for DRAM word-line recess excursions. For each symptom: likely causes ranked from most to least common, checks to separate them, and corrective actions. Chapter references point to the underlying physics.

---

## G.1 Recess Too Shallow (z_r Small; Whole Wafer)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Incoming metal top higher (less CMP     Post-CMP OCD vs. feed-forward       Fix feed-forward input;
   erosion/dishing) not fed forward        log                                 CMP review
   (Ch. 2.4, 15.5)
2. Wall loss up (W or Ti deposits;         F/Ar actinometry down; WAC-1        Extend WAC; add/verify
   WAC weak) (Ch. 9.2)                     endpoint time up                    BCl₃ step; season
3. Thick WOₓ skin (long CMP queue;         Queue time; BT W-line rise late     Enforce queue limit;
   short BT) (Ch. 4.7)                                                         lengthen BT to rule
4. New product with higher metal area      Product constant; layout area       Correct C_product
   (Ch. 3.7.4)
5. Source power low (conductive window     Delivered power; coil current;      WAC; wet clean
   film) (Ch. 5.5)                         F/Ar
```

## G.2 Recess Too Deep (z_r Large; Whole Wafer)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Pulsing fault: ME running CW            Pulse readback; V_pp pattern;       Repair generator / sync;
   (higher rate, higher k) (Ch. 6.3)       pads much deeper than array         requalify
2. Incoming metal top lower (more          Post-CMP OCD                        Feed-forward; CMP review
   erosion) not fed forward
3. Fresh walls (first wafers after clean;  Position in lot; idle time          Season; idle recovery
   no season) (Ch. 9.2.3)
4. Chamber constant wrong after reset      APC log                             Correct C_chamber
5. Wider WL CD (lot)                        CD-SEM                              Feed-forward on CD
```

## G.3 Edge Deeper Than Centre

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Gas split drift (centre fraction low)   Injector flow readback              Restore split (Ch. 7.5)
2. Edge warmer (edge-zone fault, He leak   Zone temps; He leak by zone         Restore; chuck check
   at the seal band) (Ch. 8.3)
3. Edge-ring material/wear (less F         Ring hours; ring type               Replace ring; retune
   consumption at the edge) (Ch. 9.5)
4. Low-pattern edge dies (local loading)   Die map vs. pattern                 Accept or edge tune
```

## G.4 TiN Horns After Trim (Δ_TW > +2 nm)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Trim lateral rate low (wall state,      Ti emission decay in TR slower;     Extend trim within the
   colder wafer) (Ch. 7.3.3)               STEM: tallest horns survive         window (≤ 8 s); restore T
2. TiN film more oxidized (deposition      TiN sheet resistance; XPS O;        Deposition fix; temporary
   change; long queue before W fill)       pre-trim horn larger                longer trim
   (Ch. 2.2.2, 11.1.3)
3. χ low (Cl₂ MFC drift)                   MFC calibration; Cl/Ar              Recalibrate
4. SF₆-first gas transient at ME start     Pre-flow log; arrival delays        Restore pre-flow; merge
   (Ch. 7.2.2)                                                                 lines
5. Edge only: ion tilt (ring wear);        Horn asymmetry by wall; outer 2–5   Ring replacement
   asymmetric horns (Ch. 9.5.2)            mm only
```

## G.5 TiN Pullback / Slits (Δ_TW < −1.5 nm)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. TiN faster (less O; new precursor;      TiN sheet R; pre-trim step small    Lower χ to restore a
   denser film) → no horn before trim      or negative (STEM)                  ≥ 2.5 nm pre-trim horn
   (Ch. 11.4.2)
2. χ high (SF₆ MFC low)                    MFC; F/Ar, Cl/Ar                     Recalibrate
3. Wafer warmer (ESC, He)                  Zone temps                           Restore
4. Trim too long                           Recipe audit                         Restore 6 s
Downstream: check WL–BC comb leakage and post-cap e-beam for keyhole voids
```

## G.6 TiN Veil (TiN Above the Si Surface)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. TiN top not broken through (oxidized    Queue time; BT log; STEM shows      Hold lot; review BT;
   TiN after a long CMP queue)             TiN up the mask walls               rework not possible
   (Ch. 11.2.3)                                                                after cap
2. Trim skipped or failed (plasma not      Tool log; Ti emission absent in TR  Fix; scrap or rework
   lit; recipe error)                                                          before clean
Screening: GIDL arrays massively high; row fails in sort
```

## G.7 V-Notch Deep / Seam Punch-Through

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. N₂ missing or low in ME (Ch. 12.2.3)    MFC; N₂ 337 nm emission             Restore
2. Fill seam more open (W deposition       Pre-recess TEM of the fill; lot     Deposition fix
   change)                                 dependence
3. Wafer warmer                            Zone temps                          Restore
4. Isotropic W step introduced (rework     Recipe audit                        Remove; use horn-first
   of pullback)                                                                strategy
Downstream: R_SWL up without OCD depth change (Ch. 12.6)
```

## G.8 SWD Pads Too Deep (> 75 nm)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. k up (pressure, CW, duty) (Ch. 3.3.5)   Array normal but pads deep;         Restore pulsing/pressure
                                           k from depth series
2. Pad dishing up (CMP)                    AFM pre-recess on pads              CMP fix
3. Layout (wider pads on a new product)    Design data                         Narrower pads (Ch. 10.3)
```

## G.9 Shallow Recess at Array Edge / First Word Lines

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Less CMP erosion at the boundary        OCD by WL position from edge        Dummy WLs; CMP tuning
   (Ch. 10.2.2)
2. Outer trench width (SAQP end effects)   CD-SEM of first/last trenches       Patterning correction
```

## G.10 Row-Parity Retention Pattern

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. SADP/SAQP slot widths alternate →       CD-SEM odd/even trenches; OCD by    Patterning correction;
   depth walk (Ch. 10.2.1)                 line type                           lower k
2. Odd/even WL in different CMP            Unlikely; check layout              —
   environment
```

## G.11 Retention Tail Up, Depth Normal

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Horns (effective gate edge higher)      STEM audit; GIDL arrays (BTBT ↑)    G.4
2. Gate-edge damage (bias up; trim/PT      GIDL E_a (TAT ↑); recipe audit;     Restore energy, pulsing;
   change; Ar ↑) (Ch. 13)                  V_pp                                review PT
3. Ti or W on wall oxide (trim shortened;  TOF-SIMS on test structures         Restore trim; clean
   clean changed) (Ch. 13.5)
4. Junction moved (x_j shallower)          Implant/anneal records; SIMS        Re-target z_r with x_j
5. VRT increase (H from PT)                Repeated retention tests            N₂-only PT
```

## G.12 Write (tWR) Failures Up

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Over-recess (z_r > 64)                  OCD; XRF                            G.2
2. Pullback weakening the wall edge        STEM Δ_TW                           G.5
3. Junction shallower (x_j down → less     Implant/anneal records; SIMS        Re-target z_r with x_j
   overlap at the same z_r)
4. R_SWL up (notch, cavities)              WL resistance                       G.7
```

## G.13 WL–BC Shorts

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Particle stubs (wall flakes, gas lines, E-beam VC pre-cap; adders; EDX of    WAC + BCl₃; plasma-on
   plasma-off transitions) (Ch. 9.6)       particles                           transitions; line purge
2. Keyhole voids from slits (Ch. 11.3)     STEM; post-cap e-beam              G.5
3. Horn + BC misalignment (Ch. 16.3)       Overlay data vs. fail map           G.4; overlay control
4. Recess shallow (thin cap)               OCD                                 G.1
```

## G.14 Particles Rising Over the Wet-Clean Cycle

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Ti fluoride build-up (NF₃-only WAC)     EDX: Ti, F; WAC-2 Ti emission       Add/extend BCl₃ step;
   (Ch. 9.3.1)                                                                 wet clean
2. Window film flaking                     Particle map centre-heavy; W in     Window temperature;
                                           EDX                                 WAC; wet clean
3. Gas-line corrosion                      Fe/Ni/Cr in EDX; after cylinder     Line purge; moisture
                                           change                              spec
4. Coating erosion                         Y in EDX                            Shield/coil check;
                                                                               part replacement
```

## G.15 First-Wafer Effect

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Season missing or too short             Recipe; wafer 1 vs. 2–5 offset      Restore season (Ch. 9.3)
2. Idle recovery not triggered             Idle time log                       Idle trigger (App. C.8)
3. O-rich walls after O₂ WAC step          Horn larger on wafer 1              Season after O₂ step
```

---

**Appendix G Version:** 1.0
