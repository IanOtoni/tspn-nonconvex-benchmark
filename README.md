# TSPN Non-Convex Benchmark

Public benchmark of Traveling Salesperson Problem with Neighborhoods (TSPN) instances in non-convex polygonal domains, accompanying the paper **"A GPU-Accelerated Two-Level Hybrid Approach for the Traveling Salesperson Problem with Non-Convex Neighborhoods"**, LVIII SBPO, 2026.

## Overview

Each instance places a departure point, an arrival point, and a set of polygonal neighborhoods in free space (no obstacles). Three morphology classes are provided for every instance size:

| Class | Description | Avg. edges/polygon |
|---|---|---|
| A | Convex polygons only | 8.71 |
| B | Balanced mix of convex and non-convex polygons | 9.35 |
| C | Non-convex polygons only | 10.03 |

Instance sizes (`|P|`, number of polygons): 15, 25, 35, 45, 60, 100, 150, 200, 250, 350, 500, 750, 1000, 1500, 2000.

Polygons have between 5 and 15 vertices, are randomly generated, and validated to avoid overlaps with other polygons and with the terminal points.

See [`docs/format_spec.md`](docs/format_spec.md) for the exact file format.

## Repository structure

```
tspn-nonconvex-benchmark/
├── instances/
│   ├── small/     # N <= 60
│   ├── medium/    # 60 < N <= 350
│   ├── large/     # 350 < N <= 1000
│   └── giant/     # N > 1000
├── docs/
│   └── format_spec.md
├── LICENSE-DATA   # CC BY 4.0
├── CITATION.cff
└── README.md
```

## Citation

If you use this benchmark, please cite:

```
@inproceedings{gomes2026tspn,
  author    = {Otoni, Ian and Moreira, Gabriel and de Magalh{\~a}es, Salles Viana Gomes and dos Santos, Andr{\'e} Gustavo},
  title     = {A {GPU}-Accelerated Two-Level Hybrid Approach for the {TSP} with Non-Convex Neighborhoods},
  booktitle = {Anais do LVIII Simp{\'o}sio Brasileiro de Pesquisa Operacional (SBPO)},
  year      = {2026},
  address   = {Belo Horizonte, MG, Brazil}
}
```

## License

Benchmark instances are licensed under [CC BY 4.0](LICENSE-DATA).

## Authors

- Ian Otoni Vieira Gomes — Universidade Federal de Minas Gerais
- Gabriel Moreira Marques — Universidade Federal de Viçosa
- Salles Viana Gomes de Magalhães — Universidade Federal de Viçosa
- André Gustavo dos Santos — Universidade Federal de Viçosa
