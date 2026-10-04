# Chapter 6: Ion Energy, Pulsing & Atomic-Layer Recess

## Overview

Ions do three things in the word-line recess. They make the tungsten etch directional, so that the surface goes down rather than sideways along the seam. They remove the fluoride crust from TiN, so that TiN keeps up with tungsten. And they strike the oxide around the slot, which is the one thing the recess must not damage. The energy, the energy spread, the angular spread, and the timing of the ion flux decide the balance between these effects.

This chapter covers how ion energy trades metal etch against oxide loss and damage, what the ion energy distribution looks like at 13.56 MHz bias, how synchronized pulsing reduces ARDE and charging, how the ion angular distribution sets corner shadowing, and how atomic-layer and quasi-atomic-layer recess cycles trade throughput for control.

**Learning Objectives:**
- Compare ion-enhanced yields of W, TiN, and SiO₂ versus ion energy
- Estimate damage depth in the oxide around the slot
- Describe the ion energy distribution at 13.56 MHz for light and heavy ions
- Use a flux-ratio model to explain why pulsing lowers the ARDE coefficient
- Compare CW and pulsed recess in time, width sensitivity, and pad offset
- Estimate the throughput cost of atomic-layer recess and choose where to use it

---

## 6.1 Ion Energy: Metal Versus Oxide

### 6.1.1 Yields

```
Ion-enhanced yields on halogenated surfaces (illustrative, Ar⁺-equivalent,
normal incidence):

  Energy (eV)        30      60      100     150
  ─────────────────────────────────────────────────
  W in F (W/ion)     0.8     3.1     4.5     5.5
  TiN in F           0.05    0.3     0.7     1.2     (TiFₓ sputter-limited)
  TiN in Cl          0.6     1.3     1.9     2.4     (mostly chemical)
  SiO₂ in F          0.02    0.08    0.25    0.5
  SiO₂ in Cl         ≈0      0.01    0.03    0.08

  W : SiO₂ (in F)    40      39      18      11
```

The tungsten yield rises fast up to about 60 eV and then slowly. The oxide yield in fluorine keeps rising steeply above 60 eV. The selectivity is roughly constant to 60 eV and then falls by half by 100 eV. **The recess runs near 60 eV, at the knee of the tungsten curve and below the steep part of the oxide curve.**

TiN in fluorine needs energy, because its crust must be sputtered. That is why horns grow at low energy in fluorine-rich steps, and why a chlorine-rich main step lets the energy stay low.

### 6.1.2 Damage Depth

```
Projected range of ions in SiO₂ (illustrative):
  Ion      60 eV       100 eV      150 eV
  ─────────────────────────────────────────
  F⁺       ≈ 1.4 nm    ≈ 1.9 nm    ≈ 2.4 nm
  Ar⁺      ≈ 1.0 nm    ≈ 1.4 nm    ≈ 1.8 nm
  SF₅⁺     ≈ 0.6 nm    ≈ 0.8 nm    ≈ 1.0 nm (fragments on impact)
```

The gate oxide is 3.5 nm. On the slot walls, ions arrive at grazing angles and penetrate much less than their normal range. At the top corner of the AA, where the shoulder exposes the gate oxide to nearly normal incidence for the first part of the etch, the range of 100 eV F⁺ is more than half the oxide thickness. Damage there creates traps near the gate edge, which feed trap-assisted GIDL (Chapter 13).

### 6.1.3 Choosing the Energy

```
Step     Goal                                  Mean ion energy (illustrative)
──────────────────────────────────────────────────────────────────────────────
BT       Break WOₓ and TiOₓNᵧ skins evenly      90–110 eV, short (5 s)
ME       Directional W and TiN recess, oxide   55–65 eV
         selectivity, low damage
TR       Remove TiN horns laterally, spare W   ≤ 20 eV (near-isotropic)
PT       Remove adsorbed halogen               No bias (plasma potential only)
```

---

## 6.2 The Ion Energy Distribution

### 6.2.1 Transit Time and the RF Period

The ion energy distribution (IED) at a biased electrode depends on how long an ion takes to cross the sheath compared with the RF period. Ions that cross in a fraction of a period see the instantaneous sheath voltage and arrive with a broad, bimodal spread. Ions that take many periods see the average and arrive with a narrow spread.

```
Reference main step: n_e ≈ 5×10¹⁰ cm⁻³, kT_e ≈ 3 eV, V_sh ≈ 60 V

Debye length: λ_D = 7430 √(T_e/n_e) m = 7430 √(3 / 5×10¹⁶) ≈ 5.8×10⁻⁵ m
Child-law sheath: s ≈ (√2/3) λ_D (2V/T_e)^(3/4) = 0.471 × 0.058 mm × 40^0.75
                    ≈ 0.43 mm

Ion transit time: τ_i ≈ 3s √(M / 2eV)
  Ar⁺ (40 u):   τ_i ≈ 3 × 0.43 mm × 5.9×10⁻⁵ s/m ≈ 76 ns
RF period at 13.56 MHz: τ_rf = 74 ns

τ_i / τ_rf:  F⁺ ≈ 0.7,  Cl⁺ ≈ 1.0,  Ar⁺ ≈ 1.0,  SF₅⁺ ≈ 1.8
```

At 13.56 MHz the reference ions are in the intermediate regime. The IED is bimodal, and the width shrinks with ion mass:

```
Illustrative IED widths (peak-to-peak) at ⟨E⟩ = 60 eV, 13.56 MHz:
  F⁺     ≈ 45 eV  (peaks near 38 and 83 eV)
  Cl⁺    ≈ 30 eV
  Ar⁺    ≈ 28 eV
  SF₅⁺   ≈ 15 eV
```

### 6.2.2 Why the High-Energy Peak Matters

The selectivity of Section 6.1.1 was for a single energy. With a bimodal IED, the oxide sees the high-energy peak, where its yield is several times higher, and the tungsten sees the average. For light F⁺ ions with a peak near 83 eV, the effective W:SiO₂ selectivity falls from about 39 to about 25. Three remedies are used:

```
Remedy                               Effect on IED            Cost
────────────────────────────────────────────────────────────────────────────
Higher bias frequency (27–60 MHz)    Narrows all IEDs          Less energy per W;
                                                               standing waves
Tailored (non-sinusoidal) bias       Single narrow peak at     Generator and
waveform                             set energy                match complexity
Lower energy setpoint, more ions     Lowers the high peak      Lower TiN rate in F
Ar-rich dilution                     Fewer F⁺, more heavy ions Lower F density
```

---

## 6.3 Synchronized Pulsing

### 6.3.1 The Pulse

In synchronized pulsing, the source and bias are switched on and off together at about 1 kHz:

```
Reference: f_p = 1 kHz, duty D = 50% (0.5 ms on, 0.5 ms off)

  On:   full density, ion flux, sheath at ≈ 60 V
  Off:  electron temperature falls in a few µs; electron density decays
        over ≈ 50–200 µs; negative ions (F⁻, Cl⁻) leave the core; ion flux to
        the wafer decays; radicals, which live for milliseconds or longer,
        stay nearly constant
```

### 6.3.2 Why Pulsing Lowers ARDE

Each pulse period removes only about 3 nm/s × 1 ms ≈ 0.003 nm of tungsten, about 1% of a monolayer. The surface coverage of fluorine therefore does not swing much from on to off. What pulsing changes is the time-averaged ratio of ions to radicals. The radicals stay. The ions are present only half the time.

The ARDE coefficient follows the bottom reaction probability β (k ≈ β/2, Chapter 3.2.2), and β rises with the ion-to-radical flux ratio, because ions activate surface sites that radicals then react with. A simple saturating form captures this:

```
β = β_sat × R / (1 + R),    R = c × Γ_i / Γ_F   (ion-to-radical flux ratio,
                                                  scaled)

Calibration (illustrative): CW k = 0.055 (β = 0.11); pulsed 50% k = 0.035
(β = 0.07) at the same on-phase conditions.

  Solving: R_CW ≈ 0.75, β_sat ≈ 0.26
  Pulsed:  R = 0.375 → β = 0.26 × 0.375/1.375 = 0.071 ✓
```

Pulsing lowers β because half the time the slot bottom receives radicals without ions, which builds coverage that the next on-phase uses. A lower β means the radicals are less depleted on their way down the slot, and the depth sensitivity weakens.

### 6.3.3 CW Versus Pulsed

```
Same on-phase power; reference array and pad (illustrative):

                          CW               Pulsed 50%       Pulsed 30%
─────────────────────────────────────────────────────────────────────────
ER₀ (nm/min)              250              180              140
k                         0.055            0.035            0.028
Time to z_r = 60 nm       25.0 s           32.4 s           40.6 s
Rate at end (nm/s)        2.89             2.34             1.91
∂z_r/∂w (nm/nm)           1.22             0.87             0.73
40 nm pad z_r             75.8 nm          71.9 nm          70.4 nm
```

Pulsing costs about 7 s of etch time and saves about 4 nm of pad offset and 30% of the width sensitivity. It also lowers the end rate, so each second of time error costs less depth. Lower duty helps further, but the gains shrink while the time keeps growing.

### 6.3.4 Charging and Pulsing

In the off-phase, the sheath collapses and electrons with low energy can enter the slot, neutralizing the positive charge that ions left at the bottom and the negative charge on the upper walls (Chapter 3.6). This reduces the field across the wall oxide and the deflection of ions toward one wall. It is one reason pulsed recess shows less asymmetry between the two TiN walls of a slot.

### 6.3.5 Pulsing and the TiN Corner

Pulsing does not change the geometry of corner shadowing. It does lower the ion share of the time-averaged TiN etch, which makes TiN removal more chemical and so less sensitive to shadowing. In chlorine-rich steps that is a modest gain. In fluorine-rich steps, where TiN depends on ions, pulsing at low duty slows TiN more than tungsten and makes horns worse.

---

## 6.4 Ion Angular Distribution

### 6.4.1 Collisionless Sheath

```
Ion–neutral charge-exchange mean free path at 8 mTorr (350 K gas):
  n = p / kT = 1.07 / (1.38×10⁻²³ × 350) = 2.2×10²⁰ m⁻³
  σ_cx ≈ 5×10⁻¹⁹ m²   → λ_i = 1 / (n σ) ≈ 9 mm

Sheath thickness s ≈ 0.43 mm → fraction of ions colliding ≈ s/λ_i ≈ 5%
```

Most ions cross the sheath without collision. Their angular spread comes from the transverse thermal energy at the sheath edge, σ_θ ≈ 1.2° at 60 eV (Chapter 3.5.1). The 5% that collide form a low-energy, wide-angle tail. Both parts matter for the corners:

```
Ion population           Energy     Angle      Effect in the slot
──────────────────────────────────────────────────────────────────────────
Collisionless core       ≈ 60 eV    σ ≈ 1.2°   Etches the W centre; strikes
                                               walls only near the top
Collisional tail (5%)    < 40 eV    up to 20°  Strikes upper walls; little
                                               reaches the bottom corners
```

### 6.4.2 Pressure and Angle

At 15 mTorr the collision fraction nearly doubles, and at 5 mTorr it falls to about 3%. Lower pressure gives tighter angles and less corner shadowing, but also lower radical density and a lower rate in a loaded etch. The reference 8 mTorr is a compromise. The trim step deliberately runs at higher pressure and very low bias, where the angular spread is wide, because its job is to reach the TiN horns from the side.

---

## 6.5 Atomic-Layer and Quasi-Atomic-Layer Recess

### 6.5.1 The Idea

An atomic-layer etch (ALE) splits the recess into two self-limiting half-cycles:

```
Half-cycle A (modify):  Cl₂ (or Cl radicals) adsorbs on W and TiN, no bias;
                        chlorinates the top monolayer; saturates
Purge
Half-cycle B (remove):  Ar⁺ at ≈ 40–60 eV removes the chlorinated layer;
                        saturates when the modified layer is gone
Purge

Etch per cycle (EPC), illustrative:  W ≈ 0.25 nm, TiN ≈ 0.25–0.35 nm
```

If both half-cycles saturate on both metals and at the bottom of the slot, the recess depth depends only on the number of cycles. ARDE vanishes, and the TiN–W ratio is the ratio of their EPCs, which can be close to one.

### 6.5.2 Saturation at the Slot Bottom

Saturation must hold at the bottom of an 8:1 slot, where the radical flux is lower:

```
Cl flux at the bottom at A = 8 (low-power Cl₂ plasma, illustrative):
  Γ_Cl,top ≈ 1×10¹⁷ cm⁻² s⁻¹; transmission with β ≈ 0.3 on clean W:
  Γ_bottom ≈ Γ_top / (1 + 0.3 × 8/2) ≈ 0.45 × Γ_top ≈ 4.5×10¹⁶ cm⁻² s⁻¹

Sites ≈ 1×10¹⁵ cm⁻²; sticking ≈ 0.3 → saturation time ≈ several × 
  1×10¹⁵ / (0.3 × 4.5×10¹⁶) ≈ 3 × 0.074 s ≈ 0.2 s
```

A dose half-cycle of about 0.5 s saturates the bottom with margin. The removal half-cycle needs about 0.5 s, and each purge about 0.3–0.5 s. A full cycle takes about 2 s.

### 6.5.3 The Throughput Cost

```
Full ALE recess:  85 nm / 0.25 nm per cycle = 340 cycles × 2 s ≈ 680 s
  → impractical for HVM (chamber cycle > 12 min)

ALE landing only: main recess to z ≈ 50 nm (pulsed, ≈ 28 s),
  then ALE for the last 10 nm: 40 cycles × 2 s = 80 s
  Chamber cycle ≈ 120 − 4 + 80 ≈ 196 s → 18 wafers/hour (from 30)
```

### 6.5.4 Quasi-ALE

Quasi-ALE, also called mixed-mode or rapid alternating recess, keeps the alternation but drops strict saturation. Gas and bias switch every 0.2–0.5 s, without full purges. It recovers much of the ARDE reduction and the TiN–W balance, at a rate several times that of true ALE:

```
Illustrative comparison for the last 15 nm of recess:

Mode               Rate (nm/s)   Effective k    Δ_TW drift     Time
─────────────────────────────────────────────────────────────────────
Pulsed ME          2.3–2.4       0.035          Grows (horn)   ≈ 6 s
Quasi-ALE          0.6           ≈ 0.010        Small          ≈ 25 s
True ALE           0.125         ≈ 0            ≈ 0            ≈ 120 s
```

Quasi-ALE landing is the most common compromise where the window is tight. Chapter 14 compares it with thermal and wet-like recess for future nodes.

---

## 6.6 Summary & Key Takeaways

1. **Sixty electronvolts is the knee.** Tungsten yield in fluorine saturates near 60 eV, while oxide yield keeps rising. Selectivity halves between 60 and 100 eV.

2. **The high-energy tail sets the oxide loss.** At 13.56 MHz, light F⁺ ions have a bimodal IED reaching about 83 eV. Higher frequency, tailored waveforms, and heavier ions narrow it.

3. **Pulsing lowers ARDE through the flux ratio.** Removing ions half the time lowers β and k (0.055 → 0.035), cutting the width sensitivity and pad offset at the cost of about 7 s.

4. **Pulsing also reduces charging.** Afterglow electrons neutralize the slot, which reduces wall fields and asymmetry.

5. **The sheath is nearly collisionless at 8 mTorr.** Most ions arrive within about 1° of normal. Wide angles come from a small collisional tail and from deliberate high-pressure trim.

6. **ALE trades throughput for control.** Full ALE recess takes over ten minutes. ALE or quasi-ALE for only the last 10–15 nm gives most of the benefit.

---

## Study Questions

1. Using the yield table, compute the W:SiO₂ selectivity at 45 eV and 80 eV by linear interpolation. If a bimodal IED puts half the ions at 38 eV and half at 83 eV, compute the effective selectivity and compare with a single-energy beam at 60 eV.

2. For n_e = 8×10¹⁰ cm⁻³, kT_e = 3 eV, and V_sh = 60 V, compute the sheath thickness and the transit time of Cl⁺. At what bias frequency would τ_i/τ_rf be 3?

3. Using the flux-ratio model with β_sat = 0.26 and R_CW = 0.75, compute k at duty cycles of 70% and 30%. Using the recess equation, compute the time to z_r = 60 nm and the width sensitivity for each, assuming ER₀ scales as 180 × (D/0.5)^0.5 nm/min.

4. A recipe switches from pulsed 50% to CW at the same on-phase power, and the time is shortened to 25 s. Compute the change in pad z_r and in the depth spread for a ±1.2 nm word-line CD. Is the 7 s saved worth it?

5. An ALE landing of 12 nm uses EPC = 0.3 nm and a 1.6 s cycle. Compute the added time and the new throughput from a 120 s reference cycle (assume the main step shortens by 4 s). What would quasi-ALE at 0.6 nm/s give instead?

---

**Next Chapter:** [Chapter 7: Gas Delivery, F/Cl Balance & Multi-Step Recess Recipes](./07-gas-fcl-balance-steps.md)

---

**Chapter 6 Development Status:** Complete  
**Version:** 1.0
