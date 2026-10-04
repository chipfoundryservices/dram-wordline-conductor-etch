# Appendix B: Chemistry & Reaction Data

Gas properties, bond energies, product volatility, key reactions, emission lines, and rate data for tungsten and TiN recess in fluorine–chlorine chemistry. Values are representative and intended for estimates.

---

## B.1 Process Gases

```
Gas      MW (g/mol)   Role in the recess                     Handling notes
──────────────────────────────────────────────────────────────────────────────────────
SF₆      146.06       Main F source (ME); W etch             Sulfur residue on cold
                                                             surfaces; GWP very high →
                                                             abatement
NF₃      71.00        F source (BT, WAC); W etch             Oxidizer; abatement
Cl₂      70.90        TiN etch (ME, TR); χ control           Corrosive; dry lines
                                                             (H₂O ≤ 1 ppm)
BCl₃     117.17       WAC: Ti fluoride removal by halogen     Hydrolyzes to HCl + B₂O₃;
                      exchange; O scavenger                  dry lines
N₂       28.01        ME additive (passivation, S removal);  —
                      PT
Ar       39.95        Diluent; sputter; actinometry          —
O₂       32.00        TR additive; WAC (S, C)                Low-range MFC
H₂       2.02         PT (with N₂)                            Flammable; low flow
```

---

## B.2 Bond and Formation Energies

```
Bond (mean, in the molecule)        kJ/mol      eV
──────────────────────────────────────────────────────
F–F (F₂)                            159         1.65
Cl–Cl (Cl₂)                         243         2.52
S–F (SF₆, mean)                     ≈ 327       ≈ 3.4
N–F (NF₃, mean)                     ≈ 283       ≈ 2.9
W–F (WF₆, mean)                     ≈ 510       ≈ 5.3
Ti–Cl (TiCl₄, mean)                 ≈ 430       ≈ 4.5
Ti–F (TiF₄, mean)                   ≈ 585       ≈ 6.1
B–F (BF₃, mean)                     ≈ 645       ≈ 6.7
B–Cl (BCl₃, mean)                   ≈ 445       ≈ 4.6
Si–F (SiF₄, mean)                   ≈ 565       ≈ 5.9
Si–O (SiO₂, per bond)               ≈ 450       ≈ 4.7

Standard enthalpies of formation (kJ/mol, gas unless noted):
  F 79.4; Cl 121.3; WF₆ −1722; TiCl₄ −763; TiF₄(s) ≈ −1649;
  TiN(s) −338; SiO₂(s) −911; SiF₄ −1615; BF₃ −1136; BCl₃ −403
```

---

## B.3 Product Volatility

```
Product     mp (°C)     bp / sublimation (°C)   At 50 °C wafer
─────────────────────────────────────────────────────────────────
WF₆         2           17                      Gas
MoF₆        17          34                      Gas
WOF₄        101         186                     Partly volatile (ion help)
WCl₆        275         347                     Involatile
WCl₅        248         286                     Involatile
WOCl₄       211         228                     Weak
WO₂Cl₂      —           subl. > 260             Involatile
TiCl₄       −24         136                     Volatile (vp ≈ 10 Torr at 20 °C)
TiBr₄       39          230                     Weak
TiF₄        —           subl. ≈ 284             Involatile
RuO₄        25          ≈ 40                    Volatile (toxic)
RuO₂        —           —                       Involatile
SiF₄        —           −86                     Gas
SiCl₄       −69         58                      Volatile
BF₃         −127        −100                    Gas
S (solid)   115         445                     Deposits on cold surfaces
```

---

## B.4 Key Reactions

```
Reaction                                         ΔH (kJ/mol, approx.)   Note
───────────────────────────────────────────────────────────────────────────────────
W + 6 F → WF₆                                    ≈ −2200                ME main path
W + 3 F₂ → WF₆                                   ≈ −1722                (reference)
TiN + 4 Cl → TiCl₄ + ½ N₂                        ≈ −910                 ME/TR TiN path
TiN + 2 Cl₂ → TiCl₄ + ½ N₂                       ≈ −425
TiN + 4 F → TiF₄(s) + ½ N₂                       ≈ −1630                Crust; involatile
SiO₂ + 4 F → SiF₄ + O₂                           ≈ −1020                Needs ions
TiF₄(s) + 4/3 BCl₃ → TiCl₄ + 4/3 BF₃             ≈ −90                  WAC halogen exchange
WO₃ + 2 F → WOF₄ ... (net with F, ion-assisted)  —                      BT
Ru + 2 O₂ → RuO₄(g)                              ≈ −185                 Ru recess (Ch. 14)
```

---

## B.5 Emission Lines

```
Species   Line (nm)        Use
─────────────────────────────────────────────────────────────────────
F         703.7, 685.6     Actinometry (with Ar 750.4); WAC endpoint
Cl        837.6, 725.7     χ verification
Ar        750.4, 811.5     Actinometry reference
O         777.4            TR, WAC (O₂ steps); wall O release
N₂        337.1            ME, PT (N₂ 2nd positive)
H         656.3            PT
W         400.9, 429.5     W-species level; BT clearing
Ti        498.2, 499.1,    TiN activity; WAC-2 endpoint
          500.0
B         249.7, 249.8     BCl₃ steps
S         921.3            Sulfur in SF₆ plasmas
Si        288.2            Oxide etch products (mask, walls)
```

---

## B.6 Rate Data (Reference Main Step Family)

### B.6.1 Mixing Curve

```
χ = Cl₂/(Cl₂ + SF₆); total halogen 100 sccm, N₂ 20, Ar 100; 8 mTorr;
700 W; 60 V pulsed; 50 °C. Open-area rates (nm/min), illustrative:

  χ       W        TiN      r = TiN/W     SiO₂
  ─────────────────────────────────────────────
  0.0     260      40       0.15          6
  0.2     240      90       0.38          5.5
  0.4     210      140      0.67          5
  0.6     180      175      0.97          4
  0.8     120      190      1.58          3
  1.0     35       200      5.7           1.5
```

### B.6.2 Ion-Enhanced Yields

```
Energy (eV)        30      60      100     150
───────────────────────────────────────────────
W in F             0.8     3.1     4.5     5.5
TiN in F           0.05    0.3     0.7     1.2
TiN in Cl          0.6     1.3     1.9     2.4
SiO₂ in F          0.02    0.08    0.25    0.5
SiO₂ in Cl         ≈ 0     0.01    0.03    0.08
```

### B.6.3 Temperature Coefficients at 50 °C

```
                     E_a (eV)    Thermal share    Coefficient
─────────────────────────────────────────────────────────────
W rate (ME)          0.20        ≈ 25%            +0.55%/K
TiN rate (ME)        0.15        ≈ 85%            +1.4%/K
Recess depth                                      +0.47 nm/K
TiN–W step                                        −0.74 nm/K
```

### B.6.4 Trim Rates

```
TiN lateral (horn face)          0.6 nm/s
TiN top-down in a 2 nm slit      0.3 nm/s
W (Cl₂/O₂, ≤ 20 V)               0.15 nm/s
SiO₂                             ≈ 0.0003 nm/s
```

---

## B.7 Flux Estimates

```
Thermal flux:      Γ = n v̄ / 4,  v̄ = √(8 k T / π m)
  F at 400 K:      v̄ ≈ 668 m/s; n_F = 3×10¹³ cm⁻³ → Γ_F ≈ 5.0×10¹⁷ cm⁻² s⁻¹
  Cl at 400 K:     v̄ ≈ 489 m/s
Ion flux:          Γ_i = J_i / e; 1 mA/cm² → 6.2×10¹⁵ cm⁻² s⁻¹
Metal removal:     Γ_W = ER × n_W; 3 nm/s → 1.9×10¹⁶ cm⁻² s⁻¹
Gas flow:          1 sccm = 4.48×10¹⁷ molecules/s = 1.69×10⁻³ Pa·m³/s
```

---

**Appendix B Version:** 1.0
