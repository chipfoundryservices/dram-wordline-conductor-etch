# Appendix A: Material Properties

Properties of the conductors, dielectrics, and chamber materials met in DRAM word-line recess. Values are representative room-temperature values from the literature, rounded for estimates. Thin-film values depend strongly on the deposition process and are given as typical ranges.

---

## A.1 Word-Line Conductors

```
Property                    W          Mo         Ru         TiN          n⁺ poly-Si
──────────────────────────────────────────────────────────────────────────────────────────
Molar mass (g/mol)          183.84     95.95      101.07     61.87        28.09
Density (g/cm³)             19.25      10.28      12.45      5.22 (bulk)  2.33
                                                             4.8–5.1 (ALD)
Atomic / formula-unit       6.31×10²²  6.45×10²²  7.42×10²²  5.08×10²²    5.0×10²²
  density (cm⁻³)
Melting point (°C)          3422       2623       2334       ≈ 2950       1414
Bulk resistivity (µΩ·cm)    5.3        5.3        7.1        20–25        500–1000
                                                                          (P ≈ 3×10²⁰ cm⁻³)
Electron mean free path     15–19      ≈ 14       ≈ 6.6      —            —
  (nm, estimates)
ρ·λ product (10⁻¹⁶ Ω·m²)    ≈ 8.2      ≈ 7.5      ≈ 5.1      —            —
Work function (eV)          4.5–4.6    4.5–4.7    4.7–4.8    4.4–4.7      ≈ 4.05–4.1
                                                             (O, N/Ti
                                                             dependent)
Young's modulus (GPa)       ≈ 410      ≈ 330      ≈ 450      ≈ 250–450    ≈ 160
CTE (10⁻⁶/K)                4.5        4.8        6.4        ≈ 9          2.6
Native oxide                WO₃/WO₂    MoO₂/MoO₃  RuO₂       TiOₓNᵧ       SiO₂
                            (1–2 nm    (fast,     (slow)     (0.5–1 nm)   (≈ 1 nm)
                            in hours)  thicker)
```

The ρ·λ product is the figure of merit for narrow lines. When grain-boundary and surface scattering dominate, resistivity scales roughly with ρ·λ / width, so lower ρ·λ wins at small dimensions.

---

## A.2 Thin-Film Conductors in the Reference Stack

```
Layer                       Thickness   Resistivity (µΩ·cm)   Notes
──────────────────────────────────────────────────────────────────────────────────
ALD TiN (TiCl₄ + NH₃,       2.0 nm      120–200               Cl 0.3–1 at.%, O 2–8 at.%;
  400–450 °C)                                                 density below bulk
W nucleation layer          1–2 nm      60–150                B- or Si-containing; β-W
  (B₂H₆ or SiH₄ reduction)                                    or amorphous
Bulk CVD W in a 7 nm core   ≈ 4–5 nm    15–25                 Columnar grains 3–6 nm;
  (WF₆ + H₂)                                                  seam at the centre
Reference W core (effective)  7 nm      22                    Used in Ch. 1.4.2
```

---

## A.3 Size-Dependent Resistivity (Illustrative)

Effective resistivity of a polycrystalline conductor of width w with grain size comparable to w, from combined surface (Fuchs–Sondheimer) and grain-boundary (Mayadas–Shatzkes) scattering with typical parameters:

```
Width w (nm)        5        7        10       15       30
────────────────────────────────────────────────────────────
W (µΩ·cm)           ≈ 30     ≈ 22     ≈ 16     ≈ 12     ≈ 8
Mo (µΩ·cm)          ≈ 26     ≈ 19     ≈ 15     ≈ 11     ≈ 8
Ru (µΩ·cm)          ≈ 20     ≈ 16     ≈ 13     ≈ 11     ≈ 9
(liner, nucleation layer, and seam effects included only in the W
reference value at 7 nm)
```

---

## A.4 Dielectrics

```
Property                    Thermal /     ALD SiO₂     SiN (ALD /   TEOS SiO₂
                            radical SiO₂               CVD)         (hard mask)
──────────────────────────────────────────────────────────────────────────────────
Density (g/cm³)             2.20          2.1–2.2      2.8–3.1      2.1–2.2
Dielectric constant         3.9           3.9–4.2      6.5–7.5      4.0–4.2
Band gap (eV)               ≈ 9           ≈ 8.5–9      ≈ 5.0–5.3    ≈ 8.5–9
Breakdown field (MV/cm)     > 10          8–10         6–10         6–8
Si consumed per nm of       0.44 nm       —            —            —
  oxide grown
Role in the word line       Gate oxide    Gate oxide   Cap; SAC     Hard mask; CMP
                            (grown part)  (deposited   stop         stop
                                          part)
```

---

## A.5 Silicon

```
Density 2.33 g/cm³; atomic density 5.0×10²² cm⁻³
Band gap 1.12 eV (300 K)
Oxidation: 2.5 nm grown oxide consumes 1.1 nm of Si and protrudes 1.4 nm
Reference AA: 14 nm wide at the top (Book #26), reduced by 1.1 nm per
word-line trench wall by gate oxidation
```

---

## A.6 Reference Geometry (Collected)

```
Quantity                                 Symbol     Value
───────────────────────────────────────────────────────────────────
Word-line pitch                          —          34 nm
WL trench at the Si surface              w_t        18.0 nm
Etched trench opening (pre-oxidation)    W₀         15.8 nm
Gate oxide on Si (grown + ALD)           t_ox       2.5 + 1.0 = 3.5 nm
Conductor slot in Si                     w_s        11.0 nm
Conductor slot in hard mask              —          13.8 nm
TiN liner                                t_TiN      2.0 nm
W core                                   w_W        7.0 nm (9.8 nm in mask)
Hard mask (field)                        —          30 nm SiO₂
Array erosion + dishing                  —          2 + 3 = 5 nm
Pad dishing (40 nm pads)                 —          8 nm
WL bottom (AA / isolation)               —          140 / 180 nm
Target conductor top                     z_r        60 nm (55–65)
Storage-node junction depth              x_j        62 nm
Effective conductor height               h_eff      108 nm
Sub-word-line length                     L_SWL      52 µm (1024 cells)
```

---

## A.7 Chamber Materials

```
Material         Use                    Behavior in F / Cl / metal halides
──────────────────────────────────────────────────────────────────────────────────────
Y₂O₃ (coating)   Walls, liner, window   Converts to YOF/YF₃ surface in F; stable in Cl;
                 coating                low particle release; Y contamination if eroded
YOF (coating)    Walls, liner           Pre-fluorinated; less first-wafer drift
Al₂O₃            Window body, ESC       Forms AlF₃ in F (particles); acceptable under a
                                        Y-based coating
AlN              ESC ceramic            Fluorinates slowly; He leak rises with wear
Quartz           Edge ring, injectors   Etched slowly by F (SiF₄); low F consumption
Si               Edge ring              Consumed by F (and Cl); acts as a F sink at
                                        the wafer edge
SiC              Edge ring              Intermediate consumption; longer life than Si
Anodized Al      Older liners           Cracks; Al release in Cl; avoided
Perfluoro-       O-rings                Resistant; particles if attacked by plasma
  elastomer
Stainless steel  Gas lines              Corrodes with moist Cl₂/HCl → Fe, Ni, Cr
                                        particles
```

---

## A.8 Contamination Reference

```
Element    Main source in recess          Limit, front side (cm⁻²)    Concern
──────────────────────────────────────────────────────────────────────────────────
W, Ti      Redeposition; wall flakes      < 1×10¹⁰ on wall oxide      TAT at gate edge
Y, Al      Chamber coatings               < 5×10⁹                      Oxide charge
Fe, Ni, Cr Gas lines; CMP                 < 5×10⁹                      Generation centres
Na, K      CMP; handling                  < 1×10¹⁰                     Mobile charge
Backside W, Ti                            < 1×10¹¹                     Cross-contamination

Atoms within the high-field area of one cell's gate edge (7.5×10⁻¹³ cm²)
at 1×10¹⁰ cm⁻²: ≈ 0.0075 (Ch. 13.6.3)
```

---

**Appendix A Version:** 1.0
