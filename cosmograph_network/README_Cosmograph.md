# Cosmograph Data Export

This folder contains two CSV files prepared for visualization in the [Cosmograph Web App](https://cosmograph.app/).

## Files

- **`cosmograph_edges.csv`**  
  Graph edges file with required and extra columns.

- **`cosmograph_nodes.csv`**  
  Graph nodes metadata file with styling information.

---

## `cosmograph_edges.csv`

**Required columns:**
- `source` → gene
- `target` → cell type

**Extra columns:**
- `color` → hex by regulation  
  - Upregulated = `#CC0000`  
  - Downregulated = `#0066CC`  
  - Neutral = `#888888`
- `size` → absolute log2FC scaled, clamped to [1..6]
- `regulation` → regulation status (Upregulated / Downregulated)
- `comparison` → group comparison (Infant vs Adult, Elderly vs Adult, etc.)
- `log2FC`, `p_value`, `q_value`

---

## `cosmograph_nodes.csv`

**Required column:**
- `id` → node identifier

**Extra columns:**
- `label` → same as id
- `type` → `gene` or `cell_type`
- `degree` → node degree
- `color`  
  - gene = `#2E7D32`  
  - cell type = `#FB8C00`
- `size` → scaled from degree (range ~2–14)

---

## How to Use in Cosmograph

1. Open [Cosmograph](https://cosmograph.app/).
2. Upload **`cosmograph_edges.csv`** as **Graph data**.
3. Upload **`cosmograph_nodes.csv`** as **Graph metadata** (optional but recommended).
4. Explore! You can further map node size or color to `degree`, `type`, or `regulation`.

---

## Notes

- The network is bipartite: **genes ↔ cell types**.  
- Edge color encodes up/down regulation.  
- Node color distinguishes genes (green) from cell types (orange).  
- You can extend these files with other attributes (e.g., time, pathway info).  
