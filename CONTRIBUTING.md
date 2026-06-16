# Contributing to Bollywood Data Story

Thank you for your interest in contributing! This project is a simple, visual look at the money behind Hindi cinema. Whether you want to correct a box office estimate, clarify a source, or propose a visual enhancement, all contributions are welcome.

## Suggesting Data Updates

Indian box office figures are often disputed. If you have access to a more precise, sourced figure:
1. Open a GitHub Issue to discuss.
2. Provide a public, reliable source (e.g. Ormax reports, audited figures, reliable trade analysts).
3. If approved, update the relevant CSV file in the `data/` folder and submit a Pull Request.

## Proposing Code Enhancements

This project is built to be simple and accessible. We adhere to these design principles:
- **No Build Steps**: No npm installs, Webpack/Vite bundlers, or CSS preprocessors. Just vanilla HTML, CSS, and SVG.
- **Isolated Module Scope**: Each chart runs in its own Immediately Invoked Function Expression (IIFE) to prevent global variable clashes.
- **Custom SVGs**: Charts are hand-drawn as SVG nodes using basic elements (`rect`, `circle`, `path`). Do not introduce D3.js or other charting frameworks.

### Development Process
1. Fork the repository.
2. Clone your fork locally and open `index.html` in a web browser.
3. Make changes and verify they scale nicely on mobile viewports.
4. Open a Pull Request detailing what was changed and why.

Thank you for helping tell the story of Bollywood economics!
