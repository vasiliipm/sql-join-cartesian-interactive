# SQL JOIN Visualizer

Interactive single-page tool that shows how SQL JOINs work by visualizing them as subsets of the Cartesian product of two tables.

## Idea

Any JOIN between two tables can be thought of as: take every possible pair of rows (Cartesian product), then keep only the pairs that satisfy the join condition. This tool makes that process visible — you see the full grid of all pairs, with the ones included in the result highlighted.

## Features

- **Two editable tables** (T1, T2) with configurable row counts (1–10) and integer IDs (1–10)
- **Randomize** button that fills both tables with sorted random values
- **Five JOIN types**: INNER, LEFT, RIGHT, FULL OUTER, CROSS
- **Cartesian product grid** where each cell is a `(t1.id, t2.id)` pair:
  - Blue cells — pairs included in the JOIN result
  - Orange dashed cells — NULL pairs for unmatched rows (LEFT/RIGHT/FULL OUTER)
- **Two SQL views**:
  - Standard JOIN syntax
  - Equivalent query rewritten as CROSS JOIN + WHERE filter + UNION ALL for unmatched rows
- **Result table** with the final output rows

## Usage

Open `index.html` in a browser. No build step, no dependencies.

## Screenshot

```
┌─────┬───────┬───────┬───────┐
│T1\T2│   1   │   2   │   3   │
├─────┼───────┼───────┼───────┤
│  1  │(1, 1) │(1, 2) │(1, 3) │  ← (1,1) highlighted
│  2  │(2, 1) │(2, 2) │(2, 3) │  ← (2,2) highlighted
│  4  │(4, 1) │(4, 2) │(4, 3) │  ← (4, NULL) for LEFT JOIN
└─────┴───────┴───────┴───────┘
```
