# Flow, Continuity, and Repetition (Generative Art)

This is a small, time-boxed generative art experiment. I explore flow, continuity, and implicit infinity using simple rule-based systems in Python. I focused on visual coherence rather than algorithmic complexity. The output is deterministic for a given seed.

## How it works

- The canvas is divided into a grid of cells.
- A smoothed noise field controls density, orientation, and colour regions.
- Each cell probabilistically draws a single curve.
- Most curves are symmetric Bezier S-curves (flow without start/end).
- A small fraction are Lissajous loops, introducing implicit infinity.
-Neighbouring cells share orientation to create visual coherence.

## Parameters worth tweaking

- GRID — controls overall density and scale
- coarse — size of regional patches
- Probability shaping (p = sqrt(val) vs val**2)
- Lissajous frequency (0.15)
- Palette definition

## Figure: Implicit Infinity
<img width="1550" height="1540" alt="generative_poster" src="https://github.com/user-attachments/assets/61c2c259-14b4-4bf7-bb89-cabb57b9b781" />

## Python Code
```python
"""
Generative poster: organic flow + subtle infinity symbolism

What this script does
- Creates a square canvas and divides it into a GRID x GRID set of cells.
- Builds a smooth-ish noise field over the grid.
  - The noise field controls: where marks appear, their rotation, and colour choice.
- For each cell that "passes" a probability check, draws ONE small curve:
  - Most cells: a symmetric Bezier S-curve (gives flow without obvious start/end).
  - Some cells: a Lissajous loop (figure-eight-ish motion --> implicit infinity).

Reason for this structure
- The noise field provides coherence: neighbouring cells behave similarly.
- The probability gate creates negative space without hard-edged blocks.
- A small amount of mark-type mixing (Bezier vs Lissajous) adds variation without creating focal “anchors” that stop the eye.

Tuning knobs (most important)
- GRID: more = finer detail; less = bolder marks
- coarse: smaller = larger “regions”; bigger = smaller regions
- p shaping (2 options): p = sqrt(val) -> denser; p = val**2 -> more empty space
- Lissajous rate: (random.random() < 0.15) controls how often loops appear
"""

import matplotlib.pyplot as plt
import numpy as np
import random


# Reproducibility

# Using both random and numpy random; seeding both ensures the same image
# is produced for the same seed value.
seed = 123
random.seed(seed)
np.random.seed(seed)


# Canvas / layout parameters

SIZE = 2000              # output image width/height in "data units"
GRID = 40                # number of cells along each dimension
CELL = SIZE / GRID       # size of one cell in the coordinate system

# Create a square matplotlib figure and hide axes.
fig, ax = plt.subplots(figsize=(10, 10), dpi=200)
ax.set_xlim(0, SIZE)
ax.set_ylim(0, SIZE)
ax.axis("off")

# Colour palette: gold/purple/neutral
palette = [
    "#2b2b2b",  # charcoal
    "#6a1b9a",  # deep purple
    "#9c4dcc",  # soft violet
    "#d4af37",  # gold
    "#f3e5ab",  # pale gold
]


# Noise field (controls density + rotation + colour regioning)

# The aim is a GRID x GRID field with values in [0, 1], not “TV static”.
# Strategy:
# 1) Make a small "coarse" random matrix.
# 2) Upsample it to GRID x GRID using np.kron to createblocky regions.
# 3) Smooth it slightly with a 5-neighbour average (reduces hard tiles).
#
# "coarse" sets the typical region size.
# - smaller coarse -> larger patches
# - larger coarse  -> smaller patches
coarse = 10
noise_small = np.random.rand(coarse, coarse)  # values in [0, 1)
scale = GRID // coarse                        # how many grid cells per coarse cell

# Upsample by repeating each coarse cell into a scale x scale block.
noise = np.kron(noise_small, np.ones((scale, scale)))

# Crop to exact GRID x GRID in case of rounding mismatches.
noise = noise[:GRID, :GRID]

# Smooth using immediate neighbours (up/down/left/right).
# This reduces harsh borders and helps “flow” feel continuous.
noise = (
    noise
    + np.roll(noise, 1, axis=0) + np.roll(noise, -1, axis=0)
    + np.roll(noise, 1, axis=1) + np.roll(noise, -1, axis=1)
) / 5


# Geometry helper: rotate a set of points around a center

def rotate_about(xs, ys, cx, cy, theta):
    """
    Rotate arrays of points (xs, ys) around a pivot point (cx, cy) by angle theta.

    xs, ys: 1D arrays of coordinates
    cx, cy: rotation center
    theta:  rotation angle in radians
    """
    # Standard 2D rotation matrix applied about an origin, then translated back.
    xr = (xs - cx) * np.cos(theta) - (ys - cy) * np.sin(theta) + cx
    yr = (xs - cx) * np.sin(theta) + (ys - cy) * np.cos(theta) + cy
    return xr, yr


# Main drawing loop: visit each grid cell and maybe draw a mark

for row in range(GRID):
    for col in range(GRID):
        # Cell origin (bottom-left corner in our coordinate system)
        x = col * CELL
        y = row * CELL

        # Cell centre: default anchor point for curves in that cell
        cx = x + CELL / 2
        cy = y + CELL / 2

        # Noise value for this cell: drives everything else in this cell
        val = noise[row, col]  # ~0..1

        # -------------------------------------------------------------
        # 1) Negative space / density gate
        # -------------------------------------------------------------
        # Interpret val as a probability-ish signal:
        # - higher val -> more likely to draw something in this cell
        # p = sqrt(val) biases towards drawing more often (denser fill).
        p = np.sqrt(val)
        if random.random() > p:
            # Skip drawing for this cell; creates patchy negative space.
            continue

        # -------------------------------------------------------------
        # 2) Rotation field (coherence)
        # -------------------------------------------------------------
        # Neighbouring cells have similar val -> similar theta -> local coherence.
        # Mapping val -> [0, 2π) gives a full range of orientations.
        theta = 2 * np.pi * val

        # -------------------------------------------------------------
        # 3) Colour selection (stable regions)
        # -------------------------------------------------------------
        # Map val into a palette index.
        # The exponent (0.7) biases the distribution slightly (feel free to tweak).
        idx = min(int((val ** 0.7) * len(palette)), len(palette) - 1)
        color = palette[idx]

        # -------------------------------------------------------------
        # 4) Stroke hierarchy (readability + occasional accents)
        # -------------------------------------------------------------
        # Most strokes are moderate; some are thicker/stronger accents.
        # This keeps the piece readable without introducing harsh focal points.
        if random.random() < 0.12:
            lw, alpha = 2.2, 0.9
        else:
            lw = random.uniform(0.9, 1.6)
            alpha = 0.45 + 0.35 * val  # higher val -> slightly more visible

        # -------------------------------------------------------------
        # 5) Choose curve family:
        #    - Lissajous loop (implicit infinity) occasionally
        #    - Otherwise symmetric Bezier S-curve (flow / continuity)
        # -------------------------------------------------------------
        if random.random() < 0.15:
            # ============================
            # Option 2: Lissajous loop
            # ============================
            # Lissajous curves are parametric loops defined by sine waves with
            # different frequencies. A 1:2 ratio often yields a figure-eight-ish
            # motion which reads as "infinity" without being a literal symbol.
            t = np.linspace(0, 2 * np.pi, 140)

            # Frequencies: choose 1 or 2, then enforce ratio 1:2 (or 2:4).
            a = random.choice([1, 2])
            b = 2 * a

            # Phase shift; pi/2 makes a pleasing orientation of the loop.
            delta = np.pi / 2

            # Radius controls how much of the cell the loop occupies.
            r = CELL * random.uniform(0.22, 0.36)

            # Build loop around the cell centre.
            xs = cx + r * np.sin(a * t + delta)
            ys = cy + r * np.sin(b * t)

            # Rotate the entire loop according to the local flow field.
            xs, ys = rotate_about(xs, ys, cx, cy, theta)

            ax.plot(
                xs, ys,
                linewidth=lw,
                color=color,
                alpha=alpha,
                solid_capstyle="round",  # rounded ends look softer/less “technical”
            )

        else:
            # ============================
            # Option 1: symmetric Bezier
            # ============================
            # Draw a single S-curve (cubic Bezier) inside the cell.
            # “Symmetric” here means:
            # - endpoints are mirrored around the centre line
            # - control points are mirrored too
            # This helps the curve feel continuous (no obvious start/end dominance).
            t = np.linspace(0, 1, 100)

            # Baseline offsets the endpoints up/down in opposite directions.
            # The sin(theta) term adds a directional bias tied to the flow field,
            # helping neighbouring cells "lean" together.
            baseline = CELL * np.random.uniform(-0.25, 0.25) + 0.35 * CELL * np.sin(theta)

            # Endpoints: left/right of cell centre, with mirrored vertical offsets.
            x0, y0 = x + CELL * 0.2, cy + baseline
            x3, y3 = x + CELL * 0.8, cy - baseline

            # Control points: also mirrored for a balanced S-shape.
            # Here we reuse baseline, so curvature is coherent with endpoint drift.
            x1, y1 = x + CELL * 0.35, cy + baseline
            x2, y2 = x + CELL * 0.65, cy - baseline

            # Cubic Bezier interpolation
            xs = (1 - t) ** 3 * x0 + 3 * (1 - t) ** 2 * t * x1 + 3 * (1 - t) * t ** 2 * x2 + t ** 3 * x3
            ys = (1 - t) ** 3 * y0 + 3 * (1 - t) ** 2 * t * y1 + 3 * (1 - t) * t ** 2 * y2 + t ** 3 * y3

            # Rotate curve into the local orientation field.
            xs, ys = rotate_about(xs, ys, cx, cy, theta)

            ax.plot(
                xs, ys,
                linewidth=lw,
                color=color,
                alpha=alpha,
                solid_capstyle="round",
            )


# Export

# Note: bbox_inches="tight" removes extra whitespace around the canvas.
plt.savefig(
    "figures/generative_poster.png",
    bbox_inches="tight",
    pad_inches=0,
)
plt.close()

```
