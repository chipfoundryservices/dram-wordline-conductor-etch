# Chapter 8: Wafer Temperature, Electrostatic Chucks & Radial Recess Uniformity

## Overview

The two metals in the word-line slot do not respond to temperature in the same way. The tungsten etch in the main step is mostly ion-driven, with a modest spontaneous fluorine component that speeds up with temperature. The TiN etch in a chlorine-rich step is mostly chemical and speeds up more. A warmer wafer therefore recesses slightly deeper and, more importantly, brings TiN down faster relative to tungsten. A temperature difference of a few kelvin across the wafer becomes a difference in the TiN–W step that the trim must absorb. The electrostatic chuck is where that temperature is set.

This chapter covers the temperature dependence of the recess, the heat balance of the wafer, multi-zone chucks, how depth and step are tuned radially with temperature and gas together, the thermal transients of a recipe whose steps last 5–30 s, and the health of the chuck surface in a fluorine–chlorine environment.

**Learning Objectives:**
- Estimate the temperature coefficients of W rate, TiN rate, recess depth, and TiN–W step
- Build the heat balance of a wafer during each recipe step
- Compute the wafer-to-chuck temperature difference and the thermal time constant
- Solve a two-knob radial tuning problem with gas split and edge-zone temperature
- Predict thermal transients in short steps and the first-wafer effect
- Recognize chuck-surface degradation and its signatures

---

## 8.1 Temperature Dependence of the Recess

### 8.1.1 Arrhenius Components

Each rate has a spontaneous (thermally activated) part and an ion-driven part, which depends only weakly on temperature:

```
Temperature coefficient of a thermally activated rate:
  d(ln ER)/dT = E_a / (k_B T²)

At T = 323 K (50 °C):
  E_a = 0.20 eV (W + F, spontaneous):    0.20 / (8.617×10⁻⁵ × 323²) = 2.2%/K
  E_a = 0.15 eV (TiN + Cl, chemical):    1.7%/K

Share of each rate that is thermally activated, reference ME (illustrative):
  W:    ≈ 25%  → W rate coefficient    ≈ 0.25 × 2.2% = +0.55%/K
  TiN:  ≈ 85%  → TiN rate coefficient  ≈ 0.85 × 1.7% = +1.4%/K
```

### 8.1.2 Effect on Depth and Step

```
Depth:   ∂z_r/∂T ≈ 0.55% × 85 nm ≈ +0.47 nm/K   (warmer → deeper)
Ratio:   ∂r/∂T ≈ (1.4 − 0.55)% ≈ +0.87%/K
Step:    ∂Δ_TW/∂T ≈ −0.0087 × 85 nm ≈ −0.74 nm/K  (warmer → smaller horn,
                                                    then pullback)
```

The step is almost twice as sensitive to temperature as the depth. A 2 K difference between the centre and the edge gives about 1 nm of depth difference and 1.5 nm of step difference. The step difference is the more serious, because the trim time is the same everywhere.

### 8.1.3 Other Temperature Effects

```
Effect                              Direction with higher T
──────────────────────────────────────────────────────────────────────────
Seam attack (spontaneous F down     Increases (Ch. 12)
  the seam)
Top-surface roughness               Increases slightly
WOF₄, WOCl₄ volatility              Increases → less residue
Sulfur residue                      Decreases
F diffusion into the gate oxide     Increases (Ch. 13)
Oxide etch rate (ion-driven)        Nearly unchanged
```

The reference process runs at 50 °C. Running colder would reduce seam attack but increase residue and horns. Running hotter would reduce horns and residue but increase seam attack and fluorine uptake. The useful range for TiN/W recess is about 30–70 °C.

---

## 8.2 The Heat Balance

### 8.2.1 Heat Loads

```
Heat into the wafer, reference ME (illustrative):

Source                                    Estimate                     Power
───────────────────────────────────────────────────────────────────────────────
Ion bombardment (time-averaged)           0.71 A × 75 V × 0.5 duty      27 W
Reaction heat, W + 6F → WF₆               ΔH ≈ −2200 kJ/mol;             4.4 W
                                          2.0×10⁻⁶ mol/s
Reaction heat, TiN + 4Cl → TiCl₄ + ½N₂    ΔH ≈ −910 kJ/mol;              0.8 W
                                          8.9×10⁻⁷ mol/s
Radical recombination on surfaces         F, Cl on oxide                 ≈ 0.5 W
Radiation and neutral heating from        Window, liner at 80–120 °C     ≈ 15 W
  the plasma and hot surfaces
──────────────────────────────────────────────────────────────────────────────
Total                                                                    ≈ 48 W

BT (CW, ≈ 115 V total ion energy):  ion load ≈ 0.71 × 115 ≈ 82 W → total ≈ 95 W
TR (≤ 20 V, higher pressure):       total ≈ 25 W
PT (no bias):                       total ≈ 20 W
```

### 8.2.2 Wafer-to-Chuck Temperature Difference

The wafer is cooled through a thin layer of helium between it and the chuck surface. Its effective heat transfer coefficient depends on the helium pressure and the surface roughness:

```
h_He ≈ 800 W/m²·K at 15 Torr (illustrative)
Wafer area 0.0707 m²

ΔT = Q / (h A):
  ME:  48 / (800 × 0.0707) ≈ 0.85 K
  BT:  95 / (800 × 0.0707) ≈ 1.7 K
  TR:  25 / (800 × 0.0707) ≈ 0.44 K
```

The wafer runs only about 1 K above the chuck in the main step. The heat loads are small because the bias power is small. Temperature differences across the wafer therefore come mostly from the chuck zones and the edge, not from the plasma.

### 8.2.3 Thermal Time Constant

```
Wafer mass:  ρ × A × t = 2.33 g/cm³ × 707 cm² × 0.0775 cm ≈ 128 g
Heat capacity: m c = 0.128 kg × 700 J/kg·K ≈ 90 J/K

τ = m c / (h A) = 90 / (800 × 0.0707) ≈ 1.6 s
```

A 1.6 s time constant is short compared with the 32 s main step, but not compared with the 5 s breakthrough or the 6 s trim. The wafer reaches 95% of its new temperature after about 3τ ≈ 5 s.

---

## 8.3 Multi-Zone Chucks

### 8.3.1 Zones

```
Reference chuck (illustrative):
  Zone         Radius (mm)     Heater / coolant      Setpoint range
  ─────────────────────────────────────────────────────────────────
  Centre       0–60            Heater over chiller   ±10 K around base
  Middle       60–110          Heater
  Outer        110–135         Heater
  Edge         135–150         Heater; separate He   
                               zone near the seal
  He backside: inner and outer zones; 10–20 Torr
```

### 8.3.2 The Wafer Edge

The outermost few millimetres of the wafer sit over the chuck's seal band, where the helium pressure falls to zero and the wafer contact is poorer. The edge also faces the edge ring, which is heated by the plasma and may be at 80–150 °C. Without a separate edge zone, the outer 5–10 mm of the wafer runs 1–3 K warmer than the rest, recesses about 1 nm deeper, and shows a smaller horn or a slight pullback.

### 8.3.3 Calibration

Zone setpoints are calibrated with a thermocouple wafer or a phosphor-coated wafer under a plasma load similar to the recipe. A zone that drifts by 1 K changes the step by 0.7 nm in that annulus. Recalibration after every chuck replacement and a periodic check with a calibration wafer are part of the chamber qualification (Appendix C).

---

## 8.4 Radial Tuning: Depth and Step Together

### 8.4.1 Two Outputs, Two Knobs

The radial depth profile and the radial step profile respond to the two main radial knobs differently:

```
Knob                                ∂(depth, edge − centre)   ∂(step, edge − centre)
─────────────────────────────────────────────────────────────────────────────────────
Centre-injector fraction g (per %)   −0.10 nm/%                 −0.015 nm/%
Edge-zone temperature T_e (per K)    +0.47 nm/K                 −0.74 nm/K
```

The gas split moves depth with little effect on the step. Temperature moves the step strongly and the depth moderately. Together they form a well-conditioned 2×2 system.

### 8.4.2 Worked Example

```
Measured on a new chamber (edge − centre):
  Depth difference D = +0.8 nm (edge deeper)
  Step difference S  = +1.2 nm (edge horn larger)

Solve for Δg and ΔT_e that bring both to zero:
  −0.1025 Δg + 0.47 ΔT_e = −0.8
  −0.015  Δg − 0.74 ΔT_e = −1.2

  Δg ≈ +13.9%   (centre fraction 58% → 72%)
  ΔT_e ≈ +1.34 K (edge zone 52 → 53.3 °C)
```

Heating the edge removes the edge horn but pushes the edge deeper. The gas split then pulls the edge depth back. If only temperature were used, the step would be fixed and the depth made worse. If only gas were used, the step would hardly change.

### 8.4.3 Limits

Large gas-split changes also change the edge ion flux and the edge sheath. They are best kept within about ±15% of the baseline. Large temperature offsets (more than about 5 K) create sharp radial gradients at zone boundaries, which show up as rings in the depth map.

---

## 8.5 Thermal Transients

### 8.5.1 Step-by-Step Wafer Temperature

```
Wafer temperature above chuck (τ = 1.6 s), reference recipe (illustrative):

Step   Duration   Steady ΔT    Start → end ΔT          Comment
────────────────────────────────────────────────────────────────────────────
S1     4 s        0            0 → 0                   No plasma
BT     5 s        +1.7 K       0 → +1.6 K              Not settled for the
                                                       first ≈ 2 s
S2     4 s        0            +1.6 → +0.13 K          Cools between steps
ME     32 s       +0.85 K      +0.13 → +0.85 K         Settled after ≈ 5 s
TR     6 s        +0.44 K      +0.85 → +0.46 K         Mostly settled
PT     8 s        +0.28 K      → +0.28 K
```

The transients are below 2 K and settle within each step except the breakthrough. Their main effect is on the breakthrough's uniformity and on the first seconds of the main step, both small. In this recipe the thermal transients matter less than the gas transients of Chapter 7.

### 8.5.2 First Wafer After Idle

After an idle period, the window, liner, and edge ring cool toward the chuck temperature. The first wafer sees less radiation from the walls (lower heat load) and a different wall recombination of fluorine (a chemistry effect, Chapter 9). The thermal part is small, about 0.2–0.4 K on the wafer. The chamber part, a different window and edge-ring temperature, is larger. Edge-ring temperature changes the edge fluorine and the edge rate. An idle-recovery recipe, a plasma on a dummy wafer or a waferless season of 30–60 s, restores the hardware temperatures.

---

## 8.6 Chuck Surface Health

### 8.6.1 Fluorination and Chlorination of the Chuck

The ceramic chuck surface is exposed to fluorine and chlorine during waferless cleans and whenever a wafer is not present. Its surface slowly fluorinates and roughens. This changes:

```
Change                       Signature                       Effect
──────────────────────────────────────────────────────────────────────────
Surface roughness up         He leak rate up at same          Wafer warmer;
                             pressure                         step down, depth up
Clamping force changes       Chucking voltage or current      Dechuck problems;
                             drifts                           particles on backside
Local contamination (W, Ti   Backside metal on wafers         Cross-contamination
deposits on the chuck rim)                                    to later tools
```

### 8.6.2 Monitors

```
Monitor                      Frequency          Limit (illustrative)
──────────────────────────────────────────────────────────────────────────
He leak per zone             Every wafer (FDC)   ≤ 1.5 sccm per zone
Zone heater power            Every wafer         Within ±10% of baseline
Calibration wafer            Weekly; after PM    Zones within ±0.5 K
Backside metal (TXRF)        Monthly             W, Ti < 1×10¹¹ cm⁻²
```

A rising helium leak in one zone with a matching depth and step shift in that annulus is the usual signature of chuck-surface wear. It is fixed by chuck replacement, not by recipe tuning.

---

## 8.7 Summary & Key Takeaways

1. **TiN is more temperature-sensitive than tungsten in the recess.** At 50 °C the TiN rate rises about 1.4%/K and the W rate about 0.55%/K. The step changes by about −0.74 nm/K, nearly twice the depth change of +0.47 nm/K.

2. **The plasma heats the wafer only slightly.** About 48 W in the main step raises the wafer about 0.85 K above the chuck. Radial temperature differences come from the chuck zones and the edge.

3. **The time constant is about 1.6 s.** Steps under 5 s are not thermally settled. The breakthrough is the step most affected.

4. **Depth and step need two knobs.** Gas split moves depth; edge temperature moves step. Solving both together avoids fixing one by spoiling the other.

5. **The edge is warmer unless managed.** The seal band and the hot edge ring make the outer 5–10 mm warmer, so the edge is deeper with a smaller horn. A separate edge zone corrects it.

6. **Chuck wear shows as a He leak.** A worn zone runs warmer, deepens the recess, and shrinks the horn in its annulus.

---

## Study Questions

1. Recompute the temperature coefficients of W and TiN rate, depth, and step at 30 °C and 70 °C, using the same activation energies and thermally activated shares. At which temperature is the step least sensitive to a 1 K error?

2. The bias is raised so that the time-averaged ion load in ME becomes 40 W. Compute the new total heat load, the wafer-to-chuck ΔT, and the change in step relative to the reference.

3. A chamber shows depth D = −0.6 nm and step S = +0.9 nm (edge − centre). Using the sensitivities of Section 8.4.1, compute Δg and ΔT_e. Is the solution inside the limits of Section 8.4.3?

4. The helium pressure in the outer zone falls from 15 to 10 Torr, lowering h_He there from 800 to 600 W/m²·K. Compute the change in wafer temperature at the outer zone during ME and the change in step there.

5. Why is the thermal transient in the breakthrough a smaller concern than the gas-line transient at the start of the main step? Support your answer with numbers from this chapter and Chapter 7.

---

**Next Chapter:** [Chapter 9: Chamber Walls, Metal Deposits, Seasoning & Contamination](./09-walls-metal-contamination.md)

---

**Chapter 8 Development Status:** Complete  
**Version:** 1.0
