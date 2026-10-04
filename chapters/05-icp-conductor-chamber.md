# Chapter 5: Inductively Coupled Conductor Chambers for Word-Line Recess

## Overview

The word-line recess needs a plasma that supplies a lot of fluorine and chlorine, because the wafer consumes much of what the plasma makes. It also needs ions of low and well-controlled energy, because the oxide around the slot must survive. And it must do both evenly across a 300 mm wafer that is one-sixth metal, while coating its own walls with tungsten and titanium compounds. The inductively coupled conductor-etch chamber, the same family used for gate and silicon trench etch, meets these needs because it sets plasma density and ion energy independently.

This chapter describes why this reactor type is used, how its source, bias, gas, and pumping systems map onto the recess requirements, what happens to the etch products, which materials survive a metal-halide chemistry, and how throughput and chamber matching set the size of the fleet.

**Learning Objectives:**
- Explain why ICP chambers are preferred over CCP and remote plasmas for metal recess
- Describe the coil, window, Faraday shield, gas injection, chuck, and pumping of a conductor chamber
- Estimate ion energy from bias power and ion current
- Compute residence time and the fraction of the gas that is etch product
- Explain the effect of conductive wall and window deposits on power coupling
- Compute throughput, fleet size, and the chamber-matching budget

---

## 5.1 Why an Inductively Coupled Reactor

### 5.1.1 The Requirements

```
Requirement                              Why
──────────────────────────────────────────────────────────────────────────────
High radical density (F, Cl)             Wafer consumes much of the F (Ch. 3.7);
                                         rate must stay high in a loaded etch
Low ion energy (40–100 eV)               Oxide selectivity; gate-edge damage
Ion flux high enough for anisotropy      Directional recess; seam control
Independent control of flux and energy   Tune TiN–W ratio and damage separately
Low pressure (5–15 mTorr)                Collisionless sheath; narrow ion angles
Radial tuning                            Edge loading; temperature zones
Metal-halide-compatible materials        W, Ti deposits; F and Cl attack
```

### 5.1.2 Comparison of Reactor Types

```
Reactor type          Density       Energy control       Use for WL recess
──────────────────────────────────────────────────────────────────────────────────
ICP (TCP-type)        10¹¹ cm⁻³     Independent bias     Reference; most HVM
                                    (0–150 V)
Capacitively coupled  10⁹–10¹⁰      Coupled to density   Rate too low at low
(single frequency)                  (V ≥ 200 V typical)  energy; damage
Dual-frequency CCP    10¹⁰          Partly independent   Dielectric etch tool;
                                                         rarely used for metal
Remote / downstream   Radicals only No ions              Isotropic recess options
                                                         (TiN wet-like); seam
                                                         attack (Ch. 14)
```

A capacitively coupled reactor makes ions and density with the same electrode. To get enough fluorine for a loaded tungsten etch, it must run at a power that also drives the sheath to a few hundred volts, which would etch the oxide and damage the gate edge. The ICP decouples them: the coil makes the plasma, and a separate bias generator on the chuck sets the ion energy.

---

## 5.2 Architecture

```
Schematic conductor chamber (cross-section):

           ┌───────────── coil (2 zones: inner, outer) ─────────────┐
           │   ○ ○ ○        ○ ○ ○        ○ ○ ○        ○ ○ ○        │
         ══╧═══════════ Faraday shield (slotted) ══════════════════╧══
         ▓▓▓▓▓▓▓▓▓▓▓▓▓▓ dielectric window (Al₂O₃, Y₂O₃-coated) ▓▓▓▓▓▓▓
         │        ↓ centre gas injector                              │
         │                                                           │
         │ ← edge gas                  plasma                 edge → │
         │   injectors                                     gas       │
         │                                                           │
         │ heated liner           ┌─────────────────┐                │
         │ (Y₂O₃ coating)   ┌─────┤   wafer (300)   ├─────┐ edge ring│
         │                  │     └─────────────────┘     │          │
         │                  │   ESC, 4 temperature zones  │          │
         │                  │   He backside, bias RF      │          │
         └──────────────────┴──────────┬──────────────────┴──────────┘
                                       │
                               throttle valve → turbo pump
```

### 5.2.1 Source

A planar or slightly domed two-zone coil drives the plasma at 13.56 MHz through a ceramic window. The inner/outer current ratio shifts the radial density profile. The reference recess uses 700 W, which gives an electron density near 5×10¹⁰–1×10¹¹ cm⁻³ in an SF₆/Cl₂/N₂/Ar mix. Electronegative gases lower the electron density for a given power, because negative ions replace electrons as the negative charge carriers.

### 5.2.2 Faraday Shield

A slotted conductive shield between the coil and the window blocks most of the capacitive coupling from the coil's high voltage to the plasma. Without it, the window surface under the coil would charge to tens or hundreds of volts and be sputtered. That would release aluminum or yttrium onto the wafer and wear the coating. With it, the window is bombarded at low energy, so deposits that form on it are not removed by sputtering. That has a cost, discussed in Section 5.5.

### 5.2.3 Gas Injection

A centre injector and a ring of edge injectors split the total flow. The split adjusts the radial radical profile. Because the wafer consumes fluorine, fluorine is depleted more at the centre of a fully patterned wafer than at the edge. More flow through the centre injector partly offsets this (Chapter 7).

### 5.2.4 Chuck and Bias

The electrostatic chuck clamps the wafer, controls its temperature through backside helium and zone heaters (Chapter 8), and carries the bias RF. The reference bias is 13.56 MHz, synchronized with the source for pulsing (Chapter 6).

### 5.2.5 Pumping

A turbomolecular pump with a throttle valve holds the pressure. The conductance of the path around the chuck sets how evenly the gas is pumped. Asymmetric pumping (a single side port) can tilt the radial profile. Most modern chambers pump symmetrically below the chuck.

---

## 5.3 Ion Energy From Bias Power

### 5.3.1 The Energy Balance

The bias generator delivers power mainly by accelerating ions across the sheath above the wafer:

```
⟨V_sh⟩ ≈ η P_bias / I_i

I_i = J_i × A_wafer    (plus a share of the edge ring)
η ≈ 0.6–0.8           (fraction of bias power that goes to ion acceleration;
                       the rest heats electrons and the matching network)

Reference main step (during the on-phase of pulsing):
  J_i = 1.0 mA/cm², A = 707 cm²   → I_i ≈ 0.71 A (wafer) + ≈ 0.1 A (ring)
  P_bias(on) = 80 W, η = 0.6      → ⟨V_sh⟩ ≈ 0.6 × 80 / 0.81 ≈ 59 V
  Mean ion energy ≈ 60 eV (plus the plasma potential, ≈ 15 V)
```

The bias power needed is small, tens of watts. The match and generator must be stable at that low level, because a 5 W error is a 6% error in ion energy (Chapter 15 covers delivered-power monitoring).

### 5.3.2 Ion Current Is Not Constant

The ion current depends on the source power, the gas, and the wall state. If the wall state changes the electron density by 10%, a fixed bias power changes the sheath voltage by about 10% in the other direction. For that reason, many recess recipes control the bias **voltage** (peak-to-peak or DC self-bias) rather than the bias power.

---

## 5.4 Residence Time and Etch Products

### 5.4.1 Residence Time

```
τ = p V / Q

Reference: p = 8 mTorr = 1.07 Pa; chamber volume V ≈ 40 L = 0.040 m³;
           total flow Q = 220 sccm × 1.69×10⁻³ Pa·m³/s per sccm = 0.372 Pa·m³/s

  τ = 1.07 × 0.040 / 0.372 ≈ 0.115 s
```

### 5.4.2 Etch Products in the Gas

```
From Chapter 3.7: WF₆ produced ≈ 2.7 sccm during the main step
TiCl₄ (TiN area ≈ 36% of front, rate ≈ W): ≈ 1.3 sccm
SiF₄ from mask and walls:                  ≈ 0.3 sccm

Total product ≈ 4.3 sccm in 220 sccm → ≈ 2% of the gas
```

The products are a small fraction of the gas, but they are not inert. In the plasma, WF₆ is dissociated by electron impact into WF₅, WF₄, and smaller fragments, and the F-rich gas fluorinates them back. Each product molecule is broken and rebuilt many times before it is pumped. Fragments that reach a wall where fluorine is scarce stick and build a tungsten-rich deposit. Titanium fragments meeting fluorine on the walls form TiF₃/TiF₄, which do not leave at wall temperature. These deposits are the subject of Chapter 9.

A shorter residence time (higher flow at the same pressure) lowers the product concentration and the wall deposition rate. It also lowers the fluorine utilization and raises gas cost. Recess chambers usually run near 200–300 sccm.

---

## 5.5 Conductive Deposits and Power Coupling

### 5.5.1 The Problem

Tungsten-rich and titanium-nitride-like deposits can be electrically conductive. A conductive film on the inside of the window acts as a shield between the coil and the plasma. Eddy currents in the film absorb part of the coil power and reduce what reaches the plasma:

```
Illustrative effect of a continuous conductive film on the window:
  Sheet resistance of film       Fraction of coil power reaching plasma
  > 10⁵ Ω/□                      ≈ 100% (insulating)
  10³ Ω/□                        ≈ 95%
  10² Ω/□                        ≈ 70%
  10 Ω/□                         < 30% (plasma hard to ignite)
```

Long before the film is thick enough to stop the plasma, it shifts the density by a few percent. That shifts ion current, sheath voltage at fixed power, radical density, and recess rate together. The shift is slow and monotonic over the life of a wet-clean cycle, which makes it look like a drift in the recess depth (Chapter 9).

### 5.5.2 Defences

```
Measure                          Effect
──────────────────────────────────────────────────────────────────────────
Waferless autoclean every wafer  Removes W deposits as WF₆ (NF₃/O₂) and Ti
(F step + Cl step)               deposits as TiCl₄ (Cl₂) before they build up
Heated window (80–120 °C)        Lower sticking of oxyfluorides
Bias-voltage control             Holds ion energy constant as density drifts
Source power by delivered        Compensates match losses
  power and current sensing
OES and RF trend monitoring      Detects drift before it shows in depth
```

---

## 5.6 Materials

```
Component         Material                   Risk in W/TiN recess chemistry
─────────────────────────────────────────────────────────────────────────────────
Window            Al₂O₃ with Y₂O₃ coating     Al₂O₃ → AlF₃ flakes in F;
                                             Y₂O₃ → YOF, stable
Liner / walls     Anodized Al with Y₂O₃ or   Anodization alone cracks and
                  YOF spray coating          releases Al; Cl corrodes Al
Edge ring         Si, SiC, or quartz         Si and SiC consume F (edge
                                             loading); quartz consumes less,
                                             erodes slowly
Gas injectors     Y₂O₃ or sapphire           Clogging by deposits
ESC surface       Al₂O₃ or AlN ceramic       Fluorination changes clamping
                                             and He leak
O-rings           Perfluoroelastomer         Cl and F attack; particles
```

Yttria-based coatings convert to a stable yttrium oxyfluoride in fluorine and resist chlorine. They release far fewer particles than aluminum oxide in the same environment. Their weakness is the yttrium itself, which is a contaminant on the wafer if the coating is sputtered or flakes (Chapter 9).

---

## 5.7 Throughput and Fleet Size

### 5.7.1 Cycle Time

```
Reference wafer cycle in one chamber (illustrative):
  Transfer in, clamp, pump, stabilize       25 s
  BT                                         5 s
  ME (APC-set)                              32 s
  TR                                         6 s
  PT                                         8 s
  Step transitions (4 × 3 s)                12 s
  Dechuck, transfer out                     12 s
  Waferless autoclean + season (per wafer)  20 s
  ──────────────────────────────────────────────
  Total                                    120 s  → 30 wafers/hour/chamber
```

The plasma steps are under half the cycle. The waferless autoclean, transfers, and transitions are the rest. Throughput gains come mostly from overlapping transfers and shortening the clean, not from faster etching.

### 5.7.2 Fleet

```
Fab: 100,000 wafer starts per month (DRAM)
  Required rate:  100,000 / (30 × 24) ≈ 139 wafers/hour

One recess per wafer (TiN/W word line):
  Chambers = 139 / (30 × availability 0.85 × utilization 0.90) ≈ 6.1 → 7 chambers

Two recesses per wafer (dual-work-function word line, Ch. 14):
  ≈ 12–14 chambers
```

### 5.7.3 Chamber Matching

Every chamber must produce the same recess depth and step. Typical matching contributions:

```
Source of chamber-to-chamber difference       Effect on z_r (illustrative, 3σ)
───────────────────────────────────────────────────────────────────────────────
Delivered source power and coil current       ±0.6 nm
Bias voltage calibration                      ±0.5 nm
ESC zone temperature calibration              ±0.6 nm (and ±0.9 nm in Δ_TW)
MFC accuracy (Cl₂, SF₆)                       ±0.4 nm (and ±0.5 nm in Δ_TW)
Edge-ring wear state                          ±0.5 nm (edge dies only)
Wall and window state                         ±0.7 nm
──────────────────────────────────────────────────────────────────────
RSS                                           ±1.4 nm
```

Most of this is removed by per-chamber time constants in APC (Chapter 15). What remains, about ±0.7 nm after correction, is part of the depth budget of Chapter 10.

---

## 5.8 Summary & Key Takeaways

1. **The ICP decouples density from energy.** The recess needs high radical density for a loaded etch and ion energies near 60 eV for selectivity. Only an independently biased high-density source gives both.

2. **Bias power is small.** About 80 W during the pulse on-phase gives about 60 V of sheath. Controlling bias voltage, not power, holds ion energy when the density drifts.

3. **Products are a few percent of the gas but shape the walls.** WF₆ and TiCl₄ are broken and rebuilt in the plasma, and fragments deposit where fluorine is scarce.

4. **Conductive deposits shield the coil.** A metal-rich film on the window lowers the coupled power, so per-wafer cleaning and monitoring are needed.

5. **Materials must survive F and Cl together.** Yttria-based coatings are standard. Aluminum oxide and bare anodization release particles and aluminum.

6. **Cleaning and transfers set throughput.** A 120 s cycle gives 30 wafers/hour. A 100k-wafer-per-month fab needs about seven chambers for one recess per wafer.

---

## Study Questions

1. A chamber runs at J_i = 1.2 mA/cm² with 90 W of bias in the on-phase and η = 0.65. Compute the mean sheath voltage, including 0.1 A of ion current to the edge ring. If a wall-state change lowers the ion current by 8% at fixed bias power, how much does the sheath voltage change?

2. Compute the residence time for p = 12 mTorr, V = 45 L, and Q = 300 sccm. If WF₆ is produced at 2.7 sccm, what is its mole fraction?

3. A conductive window film reduces the coupled power by 4%. Assuming the F density scales with power, the loading model of Chapter 3.7 with Φ = 1.9, and f = 0.16, estimate the change in recess rate and in z_r at fixed time.

4. The waferless autoclean is shortened from 20 s to 12 s. Compute the new throughput and the number of chambers for 100k wafers per month. What risk does this create, and how would you detect it?

5. Using the matching table, decide which single contributor you would remove first to cut the RSS most, and compute the new RSS.

---

**Next Chapter:** [Chapter 6: Ion Energy, Pulsing & Atomic-Layer Recess](./06-ion-energy-pulsing-ale.md)

---

**Chapter 5 Development Status:** Complete  
**Version:** 1.0
