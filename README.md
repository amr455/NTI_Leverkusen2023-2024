<div align="center">

# LEVERKUSEN: GOLDEN LEAGUE ANALYSIS

### Bayer 04 Leverkusen | Bundesliga 2023/24

**An event-data analysis of an unforgettable unbeaten league campaign.**

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![StatsBomb](https://img.shields.io/badge/Data-StatsBomb_Open_Data-e32636?style=for-the-badge)](https://github.com/hudl/open-data)
[![NTI](https://img.shields.io/badge/Graduation_Project-NTI-202020?style=for-the-badge)](https://www.nti.sci.eg/)

**Created by Amr Rabie**  
[LinkedIn](https://linkedin.com/in/amrrabie445)

![Leverkusen Golden League Analysis cover](assets/figures/project_cover.jpg)

</div>

---

## Project overview

This project studies Bayer 04 Leverkusen's 2023/24 Bundesliga season through StatsBomb event data. It combines team-level performance indicators, attacking and defensive visualizations, pressing analysis, and individual player insights.

The original NTI graduation presentation is organized around four stages:

1. **Data understanding and preprocessing** - reviewing the match/event tables and preparing the data for analysis.
2. **Team tactical overview** - attacking output, shot locations, defensive actions, pressing and recoveries.
3. **Player performance insights** - contributions from Florian Wirtz, the wing-backs, Granit Xhaka and Piero Hincapié.
4. **Key findings** - summarizing the team's offensive structure and defensive approach.

## Season snapshot

The figures below are the headline numbers reported in the original graduation presentation. The scripts in this repository provide a reproducible route to recalculate supported metrics from the public event data; they are not a byte-for-byte recreation of the original analysis notebook.

| Metric | Figure reported in the presentation |
|---|---:|
| Bundesliga points | **90** |
| Goals scored | **89** |
| Goals conceded | **24** |
| Expected goals (xG) | **73.6** |
| Pressures | **4,786** |

The presentation also labels Leverkusen's xG as 2nd, goals scored as 2nd, goals conceded as 1st and total pressures as 1st. Those league-wide rankings are reproduced here as source-reported claims, not recalculated by the team-only download script.

The original slides also show player examples including 3,299 passes for Granit Xhaka, 2,167 for Jonathan Tah, 22 through balls for Florian Wirtz, and 13 goals for Alejandro Grimaldo. More source-reported observations are documented in [`docs/ANALYSIS_NOTES.md`](docs/ANALYSIS_NOTES.md).

## What the analysis covers

### 1. Attacking performance

- Season shot map and shot-density view.
- Expected goals and cumulative goals context.
- Attacking locations and final-third activity.
- Player passing and chance-creation indicators.

![Attacking analysis from the NTI presentation](assets/figures/attacking_analysis.jpg)

### 2. Defensive performance and pressing

- Defensive actions and ball recoveries.
- Pressure locations and pressing activity.
- Pressing patterns in different match states (leading, drawing and trailing).
- Defensive structure and the team's ability to restrict opposition progression.

![Defensive analysis from the NTI presentation](assets/figures/defensive_analysis.jpg)

![Pressing analysis from the NTI presentation](assets/figures/pressing_analysis.jpg)

### 3. Player performance

The presentation gives individual attention to:

- **Florian Wirtz** - touch map and pass map.
- **Jeremie Frimpong and Alejandro Grimaldo** - touch and crossing maps.
- **Granit Xhaka and Piero Hincapié** - passing activity and distribution.
- Player comparisons involving dribbling and passing volume.

![Florian Wirtz maps](assets/figures/wirtz_maps.jpg)

![Wing-back touch maps](assets/figures/wingback_touch_maps.jpg)

![Wing-back crossing maps](assets/figures/wingback_cross_maps.jpg)

![Player comparison](assets/figures/player_comparison.jpg)

### 4. Team-level season picture

![Team statistics from the original presentation](assets/figures/team_stats.jpg)

## Tools and technologies

| Tool | Use in the project |
|---|---|
| Python | Data workflow and analysis |
| pandas | Filtering, cleaning, grouping and aggregation |
| StatsBomb Open Data / statsbombpy | Match and event data source |
| Matplotlib | Statistical charts |
| mplsoccer | Football pitch visualizations |
| Jupyter Notebook | Exploratory analysis and documentation |

## Repository structure

```text
leverkusen-golden-league-analysis/
├── README.md
├── requirements.txt
├── .gitignore
├── CITATION.cff
├── LICENSE
├── assets/
│   └── figures/                 # Selected visuals from the NTI presentation
├── .github/
│   └── workflows/
│       └── tests.yml
├── config/
│   └── project.json             # Competition and season identifiers
├── docs/
│   └── ANALYSIS_NOTES.md
├── data/
│   ├── raw/
│   │   └── events/              # Downloaded event files (not committed)
│   └── processed/               # Optional prepared data (not committed)
├── notebooks/
│   └── 01_analysis_walkthrough.ipynb
├── outputs/
│   ├── figures/                 # Re-generated charts
│   └── tables/                  # Re-generated CSV summaries
├── scripts/
│   ├── download_data.py
│   └── run_analysis.py
├── src/
│   └── leverkusen_analysis/
│       ├── data.py
│       ├── metrics.py
│       └── visuals.py
└── tests/
    └── test_metrics.py
```

## Run the project

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_GITHUB_USERNAME/leverkusen-golden-league-analysis.git
cd leverkusen-golden-league-analysis
```

### 2. Create an environment and install dependencies

```bash
python -m venv .venv
```

Windows:

```powershell
.venv\Scripts\activate
```

macOS / Linux:

```bash
source .venv/bin/activate
```

Install the project requirements:

```bash
pip install -r requirements.txt
```

### 3. Download the data

```bash
python scripts/download_data.py
```

The default configuration uses:

- Competition: Germany - 1. Bundesliga
- Season: 2023/2024
- `competition_id`: `9`
- `season_id`: `281`
- Team filter: `Bayer Leverkusen`

For a quick test, download two matches first:

```bash
python scripts/download_data.py --limit 2
```

To refresh previously downloaded event files:

```bash
python scripts/download_data.py --force
```

### 4. Generate tables and visualizations

```bash
python scripts/run_analysis.py
```

The script writes tables to `outputs/tables/` and charts to `outputs/figures/`.

### 5. Run the tests

```bash
pip install pytest
pytest
```

## Main generated outputs

| Output | Description |
|---|---|
| `team_season_summary.csv` | Matches, results, points, goals, xG, pressures, passes and shots |
| `match_results.csv` | Match-by-match results for Leverkusen |
| `player_passes.csv` | Pass volume by player |
| `player_through_balls.csv` | Through-ball volume by player, when the field is present |
| `player_goals.csv` | Goals by player |
| `player_dribbles.csv` | Attempted and completed dribbles |
| `team_shot_map.png` | Shot locations |
| `pressure_heatmap.png` | Locations of team pressure events |
| `wirtz_touch_map.png` / `wirtz_pass_map.png` | Wirtz event locations and passes |

## Notes on interpretation

- Event-level metrics depend on the StatsBomb event definitions and the data version available when the repository is run.
- Pass counts are event counts, not necessarily completed passes. The code keeps the distinction between attempted and completed passes where relevant.
- The team download covers Leverkusen's Bundesliga matches only. It cannot establish a Bundesliga-wide ranking unless events for every team in the competition are also collected.
- The original presentation includes additional calculations and charts. Since the original analysis notebook and prepared source files were not included with the PDF, the code here is a clean, documented reconstruction rather than a claim that every original figure has been exactly reproduced.
- Shot/pass map coordinates are displayed in StatsBomb's pitch coordinate system. Directional comparisons across halves should be normalized before drawing tactical conclusions from left/right locations.

## Data source and attribution

Data is accessed from [StatsBomb Open Data](https://github.com/hudl/open-data) using [`statsbombpy`](https://github.com/hudl/statsbombpy). StatsBomb asks researchers who publish work based on the open data to credit StatsBomb as the data source and use the StatsBomb logo from its [Media Pack](https://statsbomb.com/media-pack/). Please review the current [StatsBomb Open Data terms](https://github.com/hudl/open-data) before redistributing data or publishing derived work.

This repository contains analysis code and selected presentation visuals. It does **not** redistribute the raw StatsBomb event files. The code license in this repository does not apply to StatsBomb data, trademarks or logos.

## Author

**Amr Rabie** - Junior Data Analyst | Football Data Analyst  
[LinkedIn](https://linkedin.com/in/amrrabie445)

---

<div align="center">

*From data points to the tactical story behind an unbeaten season.*

</div>
