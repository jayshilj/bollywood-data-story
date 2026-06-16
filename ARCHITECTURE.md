# System Architecture & Technical Design

This document details the architectural decisions, design choices, and rendering logic for the **Bollywood Data Story** interactive page.

## Core Design Philosophy

- **Zero Build Tooling**: To maintain a frictionless developer environment, the project compiles no scripts or stylesheets. It serves raw HTML, standard inline CSS variables, and native browser JavaScript.
- **Dependency-Free SVG Visualizations**: Rather than loading large charting libraries (like D3.js or Chart.js) which introduce security overhead and script weight, charts are built manually using standard XML namespaces inside SVG container tags.
- **Isolated Modules (Scope Protection)**: The rendering and click control logic for each section are encapsulated within Immediately Invoked Function Expressions (IIFEs). This prevents state leaks and naming conflicts, allowing independent filter operations across charts.

## Interactive Rendering Pipeline

### 1. Panel 1: Bar Chart & Line Overlay
- Draws original Hindi collections as gradient-filled `<rect>` elements.
- Overlays the All-India box office total as a single SVG `<path>` constructed by mapping years to absolute canvas coordinates.
- COVID-19 lockouts are represented by a translucent background `<rect>` shading the 2020-2021 timeframe.

### 2. Panel 2: Scatter Plot (Log-Log Scale)
- Utilizes a standard base-10 logarithm mapping function (`Math.log10`) to scale budget (x-axis) and recovery percentage (y-axis). Log scaling prevents outliers (like *Secret Superstar* at 64× return) from rendering the rest of the dataset unreadable.
- Applies standard linear regression to derive the slope $b$ and intercept $a$ in log-space:
  $$\log_{10}(\text{recovered}) = a + b \log_{10}(\text{budget})$$
- Draws the trend line with SVG coordinates corresponding to these values.
- Filters dataset nodes visibility by toggling CSS utility classes (e.g. `.hidden`) based on selected genre sets.

### 3. Panel 3: Horizontal Stack Bar Chart
- Renders horizontal bars to represent absolute losses vs. percentage recovery.
- Re-calculates and redraws axis ticks (`drawAxis()`) dynamically upon toggling metric states.
- Utilizes invisible mouse hit-boxes (`<rect fill="transparent">`) on top of actual bars to ensure large, reliable mouse-target space.

## Shared Tooltip System

Each IIFE script handles hover coordinates locally using a bounding client rect calculation:
```javascript
const c = card(), x = e.clientX - c.left, y = e.clientY - c.top;
```
It computes boundary overlays (`tip.offsetWidth`/`tip.offsetHeight`) to prevent the tooltips from overflowing the view edges, translating positions seamlessly in log/linear layouts.
