# 🛰️ Astravynn — Orbital Intelligence & Space Situational Awareness

**Explore Earth's orbital environment through an interactive 3D globe, satellite tracking, orbital analytics, and maneuver intelligence.**

[![Live Demo](https://img.shields.io/badge/Live%20Demo-astravynn.onrender.com-00C7B7?style=for-the-badge&logo=render&logoColor=white)](https://astravynn.onrender.com/)
[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

**Live Application:** https://astravynn.onrender.com/

---

## 🌌 Overview

Astravynn is a web-based orbital intelligence dashboard designed to make satellite tracking and space situational awareness more accessible through interactive visualization and data-driven analysis.

The platform combines a 3D Earth visualization with orbital catalog data, satellite position tracking, space-weather information, and maneuver-monitoring capabilities in a unified mission-control interface.

Built as an aerospace technology and engineering project, Astravynn explores how orbital data, visualization, and analytical tools can support the monitoring of an increasingly congested space environment.

## ✨ Features

### 🌍 Live Orbital Globe
- Interactive 3D Earth visualization.
- Satellite visualization and orbital trajectories.
- Camera controls and globe navigation.
- Satellite selection and inspection.
- Continuously animated globe with interactive exploration.

### 🛰️ Orbital Eye
- Explore cataloged orbital objects.
- Search and filter satellite records.
- Inspect available orbital information.
- Visualize satellite positions using orbital propagation in the browser.

### 🎯 Maneuver Tracker
- Explore candidate orbital maneuver indicators.
- Review changes across available orbital catalog snapshots.
- Investigate potential orbital anomalies for further analysis.

*Candidate indicators are analytical outputs and are not confirmed spacecraft maneuvers unless independently verified.*

### ⚠️ Conjunction Awareness
- Explore close-approach monitoring concepts.
- Examine available orbital information relevant to conjunction assessment.
- Support further investigation of potential orbital proximity events.

### ⭐ Watchlist
- Keep track of selected orbital objects.
- Quickly return to objects of interest during dashboard exploration.

### ☀️ Space Weather
- Retrieve geomagnetic Kp information from NOAA data sources.
- Display available space-weather information alongside orbital monitoring tools.

### 🔄 Data Ingestion and Caching
- Retrieve orbital catalog data from CelesTrak.
- Cache catalog data for fallback use.
- Use a bundled catalog snapshot when live data retrieval is unavailable.
- Expose backend API endpoints for catalog access and refresh operations.

> Feature availability and data freshness depend on upstream data sources, backend status, and the current deployment environment.

## 🧰 Technology Stack

| Component | Technology |
|---|---|
| Frontend | HTML5, CSS3, JavaScript |
| 3D visualization | Three.js |
| Orbital propagation | satellite.js |
| Backend | Python |
| HTTP server | Python standard library |
| Orbital data | CelesTrak |
| Space-weather data | NOAA |
| Hosting | Render |
| Version control | Git and GitHub |

## 🏗️ Architecture

```text
                 ┌─────────────────────────┐
                 │     User's Browser      │
                 │                         │
                 │  Interactive 3D Globe   │
                 │  Orbital Eye            │
                 │  Maneuver Tracker       │
                 │  Conjunction Interface  │
                 └────────────┬────────────┘
                              │
                              ▼
                 ┌─────────────────────────┐
                 │      Python Server      │
                 │                         │
                 │  Catalog API            │
                 │  Data Refresh           │
                 │  Cache Management       │
                 └────────────┬────────────┘
                              │
                    ┌─────────┴─────────┐
                    ▼                   ▼
             ┌─────────────┐    ┌─────────────┐
             │  CelesTrak  │    │    NOAA     │
             │ Orbital Data│    │ Space Weather│
             └─────────────┘    └─────────────┘
```

The frontend renders the globe and interactive interface, while the Python backend provides catalog access and data-refresh functionality. Satellite positions can be propagated client-side using the available orbital elements.

## 📂 Project Structure

```text
astravynn/
├── index.html           # Main dashboard and frontend
├── server.py            # Python HTTP server and API
├── astra_core.js        # Core application logic
├── catalog_cache.json   # Cached orbital catalog snapshot
├── requirements.txt     # Python dependency manifest
└── vendor/              # Browser-side third-party assets
```

*The structure above describes the primary application files; additional assets may be present in the repository.*

## 🚀 Run Locally

### Prerequisites

- Python 3.x
- Git
- A modern web browser
- An internet connection for live data retrieval

### 1. Clone the repository

```bash
git clone https://github.com/techysoham/astravynn.git
cd astravynn
```

### 2. Start the application

```bash
python setup_offline.py
python server.py
```

Open the local URL printed by the server in your browser. The default server configuration uses a port in the `8000` range.

For a deployment environment such as Render, run:

```bash
python server.py --no-browser
```

The server must bind to `0.0.0.0` and use the port assigned through the `PORT` environment variable when deployed as a Render Web Service.

### 3. Explore the dashboard

Open the application and explore the globe, search for orbital objects, inspect available catalog data, and navigate through the available monitoring interfaces.

## 🌐 API Endpoints

| Endpoint | Purpose |
|---|---|
| `GET /api/catalog` | Retrieve the available orbital catalog |
| `GET /api/refresh` | Trigger or access the catalog refresh operation, depending on the server implementation |

The refresh endpoint should be used according to its implemented HTTP behavior and should not be assumed to be a read-only operation.

## ☁️ Deployment

**Live application:** https://astravynn.onrender.com/

The deployment uses a Python web service to serve the frontend and backend API from the same application.

For your own deployment:

1. Fork or clone this repository.
2. Connect the repository to Render.
3. Set the build command to `pip install -r requirements.txt`.
4. Set the start command to `python server.py --no-browser`.
5. Ensure the server binds to `0.0.0.0` and the assigned `PORT`.
6. Deploy and verify the dashboard and API endpoints.

**Deployment note:** Render's free web services may spin down after inactivity. The first request after a period of inactivity can take longer, and local filesystem changes may not persist across restarts or redeployments.

## 📡 Data Sources

- **[CelesTrak](https://celestrak.org/)** — Public orbital element and satellite catalog data.
- **[NOAA Space Weather Prediction Center](https://www.swpc.noaa.gov/)** — Space-weather and geomagnetic information.
- **[Three.js](https://threejs.org/)** — 3D graphics and globe visualization.
- **[satellite.js](https://github.com/shashwatak/satellite-js)** — Satellite orbit propagation utilities.

Data availability, catalog coverage, update intervals, and accuracy depend on the relevant upstream source and the application's implementation.

## 🛣️ Roadmap

Potential areas for future development include:

- [ ] Enhanced real-time orbital visualization and telemetry.
- [ ] Improved conjunction screening and risk assessment.
- [ ] Historical orbital snapshot storage and playback.
- [ ] Advanced maneuver analysis and recommendation workflows.
- [ ] Satellite-specific telemetry panels and orbital analytics.
- [ ] More resilient data ingestion and persistent caching.
- [ ] Automated testing and validation of orbital calculations.
- [ ] Improved deployment monitoring and observability.

## ⚠️ Limitations and Disclaimer

Astravynn is an educational and engineering project exploring orbital visualization and space situational awareness.

- Catalog data can be delayed, incomplete, or unavailable.
- Cached data may not reflect current orbital positions.
- Orbital propagation accuracy depends on the quality and age of the input elements and the propagation method.
- Candidate maneuver indicators and conjunction-related outputs require appropriate validation and should not be treated as authoritative operational assessments.
- The application is not a certified collision-avoidance or spacecraft flight-safety system.

**Do not use Astravynn as the sole basis for spacecraft maneuver execution, collision avoidance, or other operational spaceflight decisions.**

Astravynn is an independent project and is not affiliated with or endorsed by CelesTrak, NOAA, NASA, or any government space agency.

## 👨‍💻 Author

**Soham Patil**
**Sakshi Kumbhar**
**Vedika Kadam**

Computer Science & Engineering — Artificial Intelligence and Machine Learning

## 📄 License

No license has been specified yet. Unless a license is added to the repository, the default copyright rules apply to the source code.

---

*Astravynn — Visualizing the orbital environment, one satellite at a time.* 🛰️
