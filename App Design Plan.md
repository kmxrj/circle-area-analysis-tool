# 🧫 Slime Mold Area Analyzer (Local Web App)

## 🧠 Concept Overview
A **local-only web app** that lets you:
- Display a **circle** (representing a petri dish) subdivided into **millimeter-sized squares**.
- **Upload an image (PNG/JPG)** — e.g., a photo of a petri dish with slime mold.
- **Move/scale the image** to align with the circle.
- **Click grid squares** inside the circle to mark regions (like slime mold growth).
- See **total selected area**, and **two percentages**: vs. whole circle and vs. half circle.

> Runs completely in the browser, no backend or internet required.

---

## 🧰 Tech Stack

| Purpose | Tool | Notes |
|----------|------|-------|
| UI Framework | **React + Vite** | Fast setup and local dev; perfect for Cursor. |
| Canvas & Drawing | **Konva.js + react-konva** | Simplifies working with draggable images, layers, and click detection. |
| Styling | **Tailwind CSS** | Lightweight utility-first styling. |
| State Management | React Hooks | No need for Redux. |
| Math Utilities | Native JS | Simple geometry and area math. |
| File Handling | Browser File API | For local image upload. |

---

## 🧩 Core Features

1. **Circle Grid Area**
   - User-defined circle diameter (in mm).
   - Grid cell size options: **0.5mm, 1mm, 1.5mm, 2mm**.
   - Cells are strictly binary and can be toggled on/off by clicking.
   - Click detection only works inside the circle boundary.

2. **Image Layer**
   - Upload PNG/JPG.
   - Image is displayed under the grid.
   - Can be **dragged and scaled** to align with circle.
   - Optional “center image” button.

3. **Sidebar Panel**
   - Shows:
     - Selected Area (mm²)
     - Total Circle Area (mm²)
     - Percent of Full Circle (%)
     - Percent of Half Circle (%)
   - Controls:
     - Upload Image
     - Grid Size (0.5/1/1.5/2 mm)
     - Adjust Circle Diameter
     - Reset Selections

4. **Optional Enhancements**
   - (None for v1)

---

## ⚙️ Math & Area Calculations

```js
const totalCircleArea = Math.PI * r * r; // mm²
const selectedArea = selectedCells.length * (cellSize * cellSize); // mm²
const percentOfFullCircle = (selectedArea / totalCircleArea) * 100;
const percentOfHalfCircle = (selectedArea / (totalCircleArea / 2)) * 100;
```

---

## —

## 📐 Detailed Specifications

### Grid & Geometry
- Circle defined by diameter in mm; radius r = diameter / 2.
- Grid cell size options: 0.5mm, 1mm, 1.5mm, 2mm.
- Only cells whose center lies inside the circle are interactive/selectable.
- Maintain a mapping between grid indices and mm coordinates for precise area math.

### Image Alignment
- Allow user to upload PNG/JPG; render on a layer below the grid.
- Provide drag (pan) and pinch/scroll zoom for the image layer.
- Add controls: reset position and fit-to-circle.

### Selection UX
- Strictly binary cells: on/off.
- Click/tap toggles a cell; drag-to-paint (mousedown + move) toggles multiple cells.
- Modifier keys: Shift = add/paint only; Alt/Option = erase only.
- Buttons: Select All Inside Circle, Clear All, Invert Selection.
- Hover highlights cell under cursor; optional subtle grid lines for performance.

### Sidebar Metrics & Controls
- Inputs: circle diameter (mm), grid size.
- Metrics (live): selected area (mm²), total circle area (mm²), percent of full circle (%), percent of half circle (%).
- Actions: upload image, reset selections, adjust circle diameter, change grid size.

### Export & Persistence
- Not included in v1. Users can capture screenshots as needed.

### Performance
- Virtualize grid rendering via canvas/Konva shapes; avoid rendering each cell as a DOM node.
- Batch updates on drag-paint; debounce metric recomputation.
- Cap maximum grid cells (e.g., diameter up to 200mm at 1mm => ~31k cells) and warn if exceeded.

### Accessibility
- No specific requirements for v1.

### Testing & Validation
- Unit tests for geometry (point-in-circle, index-to-mm mapping) and metrics.
- Manual QA checklist for image alignment and selection tools.

### Non-Goals (v1)
- Automatic image segmentation of growth.
- Cloud storage or multi-user collaboration.
- Precise sub-cell fractional area calculation.

### Future Enhancements
- Brush sizes and lasso selection tools.
- Partial-cell area estimation via supersampling within a cell.
- Multi-region labeling and per-region statistics.