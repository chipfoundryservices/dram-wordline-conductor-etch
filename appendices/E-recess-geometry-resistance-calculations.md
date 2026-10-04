# Appendix E: Recess Geometry, Transport & Word-Line Resistance Calculations

The formulas used in this book, collected with their assumptions and worked reference values. Symbols follow the chapters. Lengths in nm unless noted.

---

## E.1 Geometry

### E.1.1 Cell Layout and the Word Line

```
6F² cell: WL pitch = 2F, BL pitch = 3F, cell area = 6F²
Reference: F = 17 → WL pitch 34, BL pitch 51, cell 1734 nm²

AA lines (pitch P normal to the line, tilted φ from the BL direction)
crossed by a WL:
  Spacing of AA lines along the WL:   P / sin(90° − φ) = P / cos φ
  Reference: 32 / cos 20° = 34.05 nm → 51/34.05 = 1.5 crossings per BL pitch
  Silicon crossing length:            W_AA / cos φ = 14 / cos 20° = 14.9 nm
  Fraction of WL over silicon:        14.9 / 51 = 0.29
```

### E.1.2 Slot Width

```
Grown oxide t_g, deposited oxide t_d, etched opening W₀:
  Si–oxide interface width:    w_t = W₀ + 2 × 0.44 t_g
  Slot in silicon:             w_s = W₀ − 2 (0.56 t_g + t_d)
  Slot in hard mask:           w_m = W₀ − 2 t_d
  W core:                      w_W = w_s − 2 t_TiN

Reference: W₀ = 15.8, t_g = 2.5, t_d = 1.0, t_TiN = 2.0
  w_t = 18.0, w_s = 11.0, w_m = 13.8, w_W = 7.0 (9.8 in the mask)
```

### E.1.3 Heights

```
Starting metal top above Si:  H₀ = t_mask − erosion − dishing
Hole depth at conductor top z: h = (t_mask − erosion) + z
Recess removed:               R = H₀ + z_r

Reference array: t_mask = 30, erosion 2, dishing 3 → H₀ = 25
  h₀ = 3, h_end = 28 + 60 = 88, R = 85, A_end = 88/11 = 8.0
```

### E.1.4 Overlap

```
Δ_ov = x_j − z_gate,  z_gate = z_r − Δ_TW (Δ_TW > 0: horn raises the edge)
Reference: x_j = 62, z_r = 60, Δ_TW ≈ 0 → Δ_ov = +2
Window: −3 ≤ Δ_ov ≤ +7 (TiN/W); −3 ≤ Δ_ov ≤ ≈ +15 (DWF, illustrative)
```

---

## E.2 Transport in a Long Slot

### E.2.1 Coburn–Winters

```
Γ_bottom / Γ_top = K / (K + β (1 − K))
K: transmission probability of the slot (lossless walls)
β: reaction probability at the bottom
```

### E.2.2 Transmission of a Long Slot (Monte Carlo)

A long slot of width w and depth L (aspect ratio A = L/w), infinitely long in the third direction, with diffuse (cosine-law) re-emission from the walls. Molecules enter the top with a cosine distribution. The table gives the probability of reaching the bottom (2×10⁵ trajectories per point, statistical error ≈ ±0.002):

```
A          0.5     1       2       3       4       6       8       10      12
──────────────────────────────────────────────────────────────────────────────────
K (MC)     0.804   0.683   0.543   0.458   0.400   0.323   0.275   0.241   0.216
1/(1+A/2)  0.800   0.667   0.500   0.400   0.333   0.250   0.200   0.167   0.143
(ln A + 0.15)/A        —       0.42    0.42    0.38    0.32    0.28    0.25    0.22
```

The simple form 1/(1 + A/2) is good below A ≈ 1 and too low above. For A ≥ 5, K ≈ (ln A + 0.15)/A within about 2%. The logarithmic behavior comes from molecules that travel long distances along the slot between wall collisions.

```python
# Long-slot transmission, diffuse walls (2D cross-section; the along-slot
# direction only lengthens paths and is projected out).
import random, math

def lambert(nx, nz):
    u, v = random.random(), random.random()
    ct, st, ph = math.sqrt(u), math.sqrt(1 - u), 2 * math.pi * v
    a = st * math.cos(ph)              # component along the in-plane tangent
    return ct * nx - a * nz, ct * nz + a * nx

def transmission(A, n=200_000):
    hits = 0
    for _ in range(n):
        x, z = random.random(), 0.0
        dx, dz = lambert(0.0, 1.0)     # enter the slot (z downward)
        while True:
            tx = (1 - x) / dx if dx > 0 else (-x / dx if dx < 0 else 1e18)
            tz = (A - z) / dz if dz > 0 else (-z / dz if dz < 0 else 1e18)
            if tz <= tx:
                hits += dz > 0
                break
            x, z = x + dx * tx, z + dz * tx
            if dx > 0:
                x = 1.0; dx, dz = lambert(-1.0, 0.0)
            else:
                x = 0.0; dx, dz = lambert(1.0, 0.0)
    return hits / n
```

### E.2.3 The Linear ARDE Form

```
With K ≈ 1/(1 + A/2):   Γ_b/Γ_t = 1/(1 + βA/2)  →  ER/ER₀ = 1/(1 + kA), k ≈ β/2

Reference fitted k = 0.035:
  simple K → β ≈ 0.07;  MC K at A = 8 → β ≈ 0.107 gives the same
  ER/ER₀ = 0.78:  0.275 / (0.275 + 0.107 × 0.725) = 0.78 ✓
```

### E.2.4 Seam Penetration

```
λ ≈ δ / √s       (δ: open seam width; s: wall reaction probability)
δ = 0.5, s = 0.01 → λ ≈ 5 nm
V-notch: tan θ = ER_ℓ / ER_v; d_V ≈ λ; w_V ≈ 2 d_V tan θ
Reference: ER_ℓ = 0.29, ER_v = 2.4 nm/s → θ ≈ 7°, w_V ≈ 1.2 nm
```

---

## E.3 Recess Time and Sensitivities

```
dh/dt = ER₀ / (1 + k h / w)
ER₀ t = (h − h₀) + (k / 2w)(h² − h₀²)

Solution for h at given exposure X = ER₀ t:
  a = k / 2w
  h = [−1 + √(1 + 4a (X + h₀ + a h₀²))] / (2a)

Width sensitivity at fixed t:
  ∂h/∂w = [k (h² − h₀²) / 2w²] / (1 + k h / w)

Rate at the end:  ER_end = ER₀ / (1 + k h_end / w)

Reference (k = 0.035, w = 11, ER₀ = 3.0 nm/s, h₀ = 3, h_end = 88):
  X = 85 + 12.31 = 97.3 nm → t = 32.4 s
  ER_end = 2.34 nm/s;  ∂h/∂w = 0.87
  With BT (to h = 4) and trim (≈ 0.9 nm): ME from h = 4 to 87 → 31.7 s
```

### E.3.1 Pad Example

```
w = 40, h₀ = 8, mask top 29; X = 97.3
a = 0.035/80 = 4.375×10⁻⁴
h = [−1 + √(1 + 4a (97.3 + 8 + a × 64))] / (2a) = 100.9 → z_r = 71.9
```

### E.3.2 Pulsing (Flux-Ratio Model)

```
β = β_sat R / (1 + R); R ∝ duty × Γ_i/Γ_F
Calibration: β_sat = 0.26, R_CW = 0.75 → k(CW) = 0.055, k(50%) = 0.035
k(30%): R = 0.225 → β = 0.048 → k ≈ 0.024 (Ch. 6.3.3 uses a fitted 0.028)
```

---

## E.4 Loading

```
ER(f) = ER(0) / (1 + Φ f)
Φ = k_wafer(f = 1) / (k_p + k_w)

Reference: f = 0.16, Φ = 1.9 → ER/ER(0) = 0.77

Wall-loss change ε (fractional, of k_p + k_w):
  ER_new / ER = (1 + Φ f) / (1 + ε + Φ f)
  ε = 0.05 → 1.30/1.35 = 0.963 → −3.7% → ≈ −3.1 nm over 85 nm
```

---

## E.5 Step (TiN–W)

```
Δ_TW = ∫₀^R [1 − r(h)] dh;   r(h) = r_open [1 − s_i (1 − c(h))]

Reference: r_open = 0.97, s_i = 0.12, c from 1.0 to 0.6 (mean 0.8):
  r_avg = 0.947 → Δ_TW = 0.053 × 85 = +4.5 nm (pre-trim)

Trim: t_clear = t_TiN / ER_lat = 2.0/0.6 = 3.3 s
  Post-trim Δ_TW = −(ER_slit − ER_W)(t_trim − t_clear)
               = −(0.3 − 0.15)(6 − 3.3) = −0.4 nm
```

---

## E.6 Word-Line Resistance

```
h_eff = f_Si (h_AA) + (1 − f_Si)(h_iso)
  h_AA = 140 − z_r, h_iso = 180 − z_r, f_Si = 0.29
  Reference: 0.29 × 80 + 0.71 × 120 = 108 nm

A_W   = w_W × h_eff;  A_TiN = 2 t_TiN h_eff + t_TiN w_s
R′    = 1 / (A_W/ρ_W + A_TiN/ρ_TiN)

Reference: ρ_W = 22 µΩ·cm, ρ_TiN = 150 µΩ·cm
  A_W = 756 nm², A_TiN ≈ 454 nm²
  R′_W = 291 Ω/µm, R′_TiN ≈ 3300 Ω/µm → R′ = 267 Ω/µm
  R_SWL = 267 × 52 = 13.9 kΩ

Recess sensitivity: R ≈ R_ref × h_eff,ref / (h_eff,ref − Δz_r) → +0.9%/nm
RC delay (distributed, far end, 50%): t ≈ 0.38 R C = 0.38 × 13.9 kΩ × 150 fF
  ≈ 0.79 ns

Liner-free metal filling w_s: R′ = ρ / (w_s h_eff)
  Ru, 14 µΩ·cm: 1.4×10⁻⁷ / (11 × 108 × 10⁻¹⁸) ≈ 118 Ω/µm
```

---

## E.7 Device and Retention

```
GIDL (illustrative):    I(Δ) = I(+2) × 10^((Δ − 2)/8)
I_on (illustrative):    I_on(Δ) = I_on,0 [1 − 0.04 max(0, −Δ)]

Retention budget:       I_max = 0.4 × C_s (V_DD/2) / t_REF
  C_s = 8 fF, V_DD = 1.1 V, t_REF = 64 ms → 28 fA

Single trap:            I = q e_n; e_n = 10⁵ s⁻¹ → 16 fA
Tail cells per die:     N = n_k × A_edge × N_cells
  n_k = 10⁶ cm⁻², A_edge = 7.5×10⁻¹³ cm², N = 1.72×10¹⁰ → ≈ 13,000
```

---

## E.8 Thermal

```
d ln ER / dT = E_a / (k_B T²)
  0.20 eV at 323 K → 2.2%/K;  0.15 eV → 1.7%/K
ΔT (wafer–chuck) = Q / (h_He A);  h_He ≈ 800 W/m²·K, A = 0.0707 m²
τ = m c / (h_He A) = (0.128 × 700) / (800 × 0.0707) ≈ 1.6 s
```

---

## E.9 Sheath and Ions

```
λ_D = 7430 √(T_e[eV] / n_e[m⁻³]) m
s ≈ (√2/3) λ_D (2V/T_e)^(3/4)                    (Child law)
τ_i ≈ 3 s √(M / 2eV);  τ_rf = 1/f
σ_θ ≈ √(kT_i / 2eV)
⟨V_sh⟩ ≈ η P_bias / I_i
λ_i = 1/(n σ_cx); collision fraction ≈ s/λ_i

Reference: n_e = 5×10¹⁰ cm⁻³, T_e = 3 eV, V = 60 V → λ_D ≈ 58 µm,
  s ≈ 0.43 mm, τ_i(Ar⁺) ≈ 76 ns, σ_θ ≈ 1.2°, λ_i ≈ 9 mm (8 mTorr)
```

---

**Appendix E Version:** 1.0
