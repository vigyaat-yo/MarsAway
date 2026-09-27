# MARSWAY — Mars Mission Navigator

MARSWAY is an interactive Mars terrain and route-planning prototype built for a hackathon.

The project combines real MOLA terrain data, terrain analysis, risk-aware path planning, and a CesiumJS 3D Mars globe to explore how autonomous missions could plan safer routes across the Martian surface.

## Features

- 🌍 Interactive 3D Mars globe
- 🛰️ Real MOLA elevation data
- 🗺️ Global Mars terrain mesh
- 📐 Terrain slope calculation
- ⚠️ Terrain hazard/risk calculation
- 🤖 Risk-aware A* route planning
- 🚀 Mission route visualization
- 🔬 Jezero Crater exploration area
- ⚡ React + TypeScript frontend
- 🐍 FastAPI Python backend

## Tech Stack

### Frontend

- React
- TypeScript
- Vite
- CesiumJS

### Backend

- Python
- FastAPI
- NumPy

### Terrain & Geospatial Data

- NASA/JPL MOLA-derived terrain data
- Raster terrain processing
- Slope analysis
- Risk mapping
- A* pathfinding

## Project Structure

```text
project-atlas/
├── backend/
│   ├── main.py
│   └── route_engine.py
│
├── data/
│   ├── raw/
│   └── processed/
│
├── scripts/
│   ├── load_terrain.py
│   ├── route_planner.py
│   └── export_global_terrain.py
│
├── src/
│   ├── components/
│   │   └── MarsGlobe.tsx
│   └── App.tsx
│
├── LICENSE
├── README.md
├── package.json
└── vite.config.ts
````

## Current Prototype

The current prototype includes a global MOLA terrain mesh rendered directly in CesiumJS.

The terrain pipeline currently:

1. Loads MOLA elevation data.
2. Extracts and processes terrain grids.
3. Calculates terrain slope.
4. Converts slope into a terrain-risk value.
5. Uses the risk data in an A* route planner.
6. Exposes terrain and route information through a FastAPI backend.
7. Visualizes Mars terrain and mission routes in CesiumJS.

## Running the Project

### Frontend

Install dependencies:

```bash
npm install
```

Start the frontend:

```bash
npm run dev
```

The Vite development server will provide the local frontend URL.

### Backend

Activate the Python virtual environment and start FastAPI:

```bash
python -m uvicorn backend.main:app --reload
```

The backend provides terrain and route endpoints used by the frontend.

## API

### Terrain

```text
GET /terrain
```

Returns information about the processed Jezero terrain grid, including elevation, slope, and risk statistics.

### Route

```text
GET /route
```

Runs the risk-aware A* route planner and returns a mission route together with route risk metrics.

## Terrain Data

MARSWAY uses Mars elevation data derived from the Mars Orbiter Laser Altimeter (MOLA) dataset.

The project processes the source terrain data into smaller grids suitable for analysis and browser visualization.

Raw and processed terrain files are kept under:

```text
data/raw/
data/processed/
```

## Route Planning

The route planner uses A* pathfinding.

Movement cost includes both distance and terrain risk:

```text
movement cost = 1 + terrain risk
```

This allows the planner to prefer routes that avoid higher-risk terrain rather than considering distance alone.

## Mission Area

The primary demonstration area is:

**Jezero Crater, Mars**

Approximate center:

```text
Latitude: 18.44° N
Longitude: 77.45° E
```

## Roadmap

* [x] Mars 3D globe
* [x] MOLA terrain processing
* [x] Global terrain visualization
* [x] Jezero terrain analysis
* [x] Slope calculation
* [x] Terrain risk calculation
* [x] Risk-aware A* routing
* [x] FastAPI terrain endpoint
* [x] FastAPI route endpoint
* [x] Cesium route visualization
* [ ] Interactive elevation layer
* [ ] Interactive slope layer
* [ ] Interactive terrain-hazard layer
* [ ] Science target visualization
* [ ] Perseverance mission context
* [ ] AI-assisted mission explanation
* [ ] PostgreSQL/PostGIS integration

## License

This project is licensed under the MIT License.
