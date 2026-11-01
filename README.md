# PixelPress — Offline Image Compressor

> A lightweight, zero-dependency client-side image compression tool inspired by Google's Squoosh. Built entirely with vanilla HTML5, CSS, and JavaScript.

[![License: MIT](https://img.shields.io/badge/License-MIT-purple.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Web%20Browser-blue.svg)](#)
[![Dependencies](https://img.shields.io/badge/Dependencies-Zero-green.svg)](#)

---

## Overview

**PixelPress** is an anti-AI-wrapper image optimization utility designed to run 100% inside your browser. Modern image tools often rely on costly server infrastructure, monthly subscription tiers, or rate-limited cloud APIs. PixelPress eliminates all external dependencies by using standard browser APIs (`HTMLCanvasElement.toBlob()`) to compress, convert, and resize images locally[cite: 2].

Your images never leave your machine — ensuring zero latency, zero server costs, and complete privacy[cite: 2].

---

## Features

- **Interactive Comparison Slider**: A split-screen before/after viewport powered by CSS `clip-path` and the Pointer Events API with full keyboard support (`Arrow`, `Shift+Arrow`, `Home`, `End`)[cite: 2].
- **Format-Aware Compression**:
  - **JPEG**: Adjustable lossy quality (0–100%) with automated white background fill to prevent transparent pixels from turning black[cite: 2].
  - **WebP**: High-efficiency modern compression with alpha channel preservation[cite: 2].
  - **PNG**: Lossless optimization with automatic quality slider dimming[cite: 2].
- **Dimension Resizing**: Custom width and height adjustments with an aspect-ratio lock toggle and dimension bounds checks (1 px to 16,384 px)[cite: 2].
- **Real-Time Performance**: Enforces a 280 ms debounce window during slider interaction to maintain a smooth 60 FPS UI without freezing[cite: 2].
- **Memory-Safe Operation**: Automatically revokes Blob Object URLs on re-upload, recompression, and file download to prevent browser memory leaks[cite: 2].
- **Live File Metrics**: Instant visual readouts calculating original file size, compressed size, bytes saved, and reduction percentage[cite: 2].

---

## Technical Specifications

| Component | Implementation |
| :--- | :--- |
| **Architecture** | Single-page application (`index.html`)[cite: 2] |
| **Engine** | Native `HTMLCanvasElement.toBlob()`[cite: 2] |
| **UI Styling** | Modern Dark Mode, CSS Glassmorphism, Inter typeface[cite: 2] |
| **Accessibility** | Semantic ARIA attributes, `role="slider"`, visible focus indicators[cite: 2] |
| **Supported Inputs** | JPEG, PNG, WebP, GIF, BMP[cite: 2] |
| **Supported Exports** | JPEG, WebP, PNG[cite: 2] |

---

## How It Works

```text
[ User Image ] 
       │
       ▼
[ FileReader API ] ──► [ Off-screen Canvas ]
                               │
       ┌───────────────────────┴───────────────────────┐
       ▼                                               ▼
[ Aspect Ratio / Bounds ]                    [ toBlob() Encoding ][cite: 2]
                                                       │
                               ┌───────────────────────┴───────────────────────┐
                               ▼                                               ▼
                     [ Real-Time File Stats ]                        [ CSS clip-path Split View ][cite: 2]
