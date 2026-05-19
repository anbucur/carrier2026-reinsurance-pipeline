# CARRIER 2026 - Reinsurance Pipeline Simulation

## Overview
Self-contained HTML dashboard simulating a reinsurance pipeline for "CARRIER 2026" Global Insurance Program. Built with React 18, Babel (JSX in-browser), and Tailwind CSS via CDN. No build step required.

## Architecture
- **Single file**: `index.html` (~740 lines) — everything in one file
- **CDN deps**: React 18, ReactDOM 18, Babel standalone, Tailwind CSS
- **State**: React hooks + localStorage for persistence
- **No build step**: open `index.html` directly in browser

## Key Concepts
- **Pipeline flow**: Inward Policy → MGA Engine (fee calc) → Distribution (insurers + local fronts)
- **Lead Insurer**: configurable via dropdown, absorbs risk directly from Master Policy
- **Co-insurers**: receive risk via outward policies (retrocession)
- **Lead Fee**: 4 modes — percentage/fixed × repeating/one-time
- **Ceding Fee**: percentage with minimum floor
- **Party roles**: Ceding Company, Reinsured, Lead Reinsurer, Co-insurer, Retrocedant, Retrocessionaire

## Tab Structure
1. **Pipeline** (default): 3-column simulation view with animated flow
2. **Hierarchy**: CSS tree showing Master Policy → Insurers → Policies
3. **Setup**: Configurable insurers, fronts, fees, presets (localStorage)

## Design System
- Dark theme (Material Design 3 inspired)
- Colors: green/blue/violet spectrum (sky, emerald, teal, violet, indigo, cyan)
- No orange/yellow/red for UI elements
- All currencies EUR (de-DE locale)
- Layout: full viewport width (`max-w-[95vw]`)

## localStorage
- Key: `carrier2026-setups-v2`
- Stores named presets with full configuration

## Color Mapping (INS_COLORS)
1. Sky blue — Insurer #1 (lead default)
2. Emerald — Insurer #2
3. Violet — Insurer #3
4. Teal — Insurer #4
5. Indigo — Insurer #5
6. Cyan — Insurer #6

## Simulation Phases
`IDLE → INWARD → FEE_CALC → DISTRIBUTE → COMPLETE`
- Timed transitions: INWARD(1.2s) → FEE_CALC(1.5s) → DISTRIBUTE(auto) → COMPLETE(manual reset)

## Development
```bash
# Just open in browser
open index.html

# Or serve locally
npx serve .
```
