# Instance File Format

Each instance is stored in a single plain-text file, named as `<Block>_<N>_<Type>.txt`:

- `Block` ∈ {Small, Medium, Large, Giant} — scalability block (N ≤ 60, 60 < N ≤ 350, 350 < N ≤ 1000, N > 1000)
- `N` — number of polygonal neighborhoods in the instance
- `Type` ∈ {A, B, C} — morphology class (A: convex only, B: mixed, C: non-convex only)

Example: `Small_35_A.txt` → Small block, 35 neighborhoods, type A.

## Line-by-line format

```
<instance_name>
<departure_x> <departure_y>
<arrival_x> <arrival_y>
<num_vertices_bbox> <x1> <y1> ... <xM> <yM>
<num_polygons>
<num_vertices_1> <x1> <y1> ... <xK> <yK>
<num_vertices_2> <x1> <y1> ...
...
<num_vertices_num_polygons> <x1> <y1> ...
```

1. **Line 1** — instance name (matches the file name without extension).
2. **Line 2** — departure point coordinates (`x y`).
3. **Line 3** — arrival point coordinates (`x y`).
4. **Line 4** — legacy bounding polygon: vertex count followed by that many `(x, y)` pairs. Currently always a 4-vertex axis-aligned bounding box enclosing departure, arrival, and all neighborhoods. **Not used** by the reference reader/solver; kept in the current file format for backward compatibility and may be removed in a future release.
5. **Line 5** — number of polygonal neighborhoods, `|P|` (matches `N` in the file name).
6. **Following `|P|` lines** — one polygon per line: vertex count followed by that many `(x, y)` pairs, listed in boundary order.

## Example

Excerpt from `Small_35_A.txt`:

```
Small_35_A
1440.90 559.11
856.19 1767.09
4 0.00 0.00 2400.00 0.00 2400.00 2400.00 0.00 2400.00
35
9 2158.04 1876.99 2143.97 1819.06 2162.27 1793.03 ...
10 1727.23 849.36 1729.21 827.49 1754.79 812.45 ...
...
```

## Notes

- Departure and arrival are single points, not polygons with area.
- Polygons have between 5 and 15 vertices.
- No obstacles are present in any instance.
- Coordinates are floating-point values with no fixed unit or bounded range beyond the bounding box on line 4.
