# AIS Anomaly Console — Vessel Behaviour Analysis🚢⚓

A self-contained interactive dashboard for exploring anomalous vessel behaviour detected from AIS (Automatic Identification System) data using machine learning.

**Dataset:** NOAA MarineCadastre — 17 December 2019 (UTC)
**Output:** Single `dashboard.html` file with all data embedded .

## Preview

Open `dashboard.html` in any modern browser. The dashboard works offline (only the map tiles and a few CDN libraries need internet).

## Features

- **Headline KPIs** — anomalous vessels detected, mean anomaly score, most extreme outlier, vessel groups represented.
- **Interactive map** (Leaflet + CartoDB dark tiles) showing each anomalous vessel's centroid, colored by anomaly score.
- **Score distribution** histogram and **vessel-group breakdown** (pleasure, cargo, fishing, tanker, etc.).
- **Top 5 outliers** quick list with MMSI, name and score.
- **Filters & controls:**
  - Filter by vessel group
  - Minimum anomaly score slider
  - Search by vessel name / MMSI
  - Configurable X / Y axes for the feature scatter plot
- **Feature scatter plot** (Plotly) — pick any two engineered features, and colour encodes the anomaly score.
- **Sortable vessel table** with all engineered features:
  MMSI, Name, Group, Type, Score, Signals, Duration (h), Avg/Max/Std speed, Total distance (km), Bounding-box diagonal (km), Max time gap (s), Sudden jumps, Centroid lat/lon.

## How it works

1. Raw AIS pings for the day are grouped by MMSI (one row per vessel).
2. For each vessel, a feature vector is computed:
   - signal count, duration, average / max/std speed
   - total distance, bounding-box diagonal
   - max time gap between pings, count of sudden position jumps
   - centroid lat/lon
3. An **Isolation Forest** is fit over these features; lower scores = more anomalous.
4. The resulting table is embedded into `dashboard.html` and rendered interactively.


## Usage

```bash
# Just open the file
start dashboard.html        # Windows
open dashboard.html         # macOS
xdg-open dashboard.html     # Linux
```

No installation, no dependencies to install — everything is bundled.

## File structure

```
.
└── dashboard.html   # Self-contained dashboard (HTML + CSS + JS + embedded data)
```

## Data source

- [NOAA MarineCadastre AIS data](https://marinecadastre.gov/ais/) — 2019-12-17

## License

Data © NOAA MarineCadastre. Map tiles © CartoDB / OpenStreetMap contributors.
Code released for educational / research purposes.

---

Let me know if you'd like an Arabic version, a shorter version, or screenshots/badges added.# AIS-dashboard
