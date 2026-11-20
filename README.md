LEVERKUSEN: GOLDEN LEAGUE ANALYSIS
Bayer 04 Leverkusen | Bundesliga 2023/24
An event-data analysis of an unforgettable unbeaten league campaign.



Created by Amr Rabie
LinkedIn

</div>Project overview
This project studies Bayer 04 Leverkusen's 2023/24 Bundesliga season through StatsBomb event data. It combines team-level performance indicators, attacking and defensive visualizations, pressing analysis, and individual player insights.

The original NTI graduation presentation is organized around four stages:
1. Data understanding and preprocessing - reviewing the match/event tables and preparing the data for analysis.
2. Team tactical overview - attacking output, shot locations, defensive actions, pressing and recoveries.
3. Player performance insights - contributions from Florian Wirtz, the wing-backs, Granit Xhaka and Piero Hincapié.
4. Key findings - summarizing the team's offensive structure and defensive approach.
Season snapshot
The figures below are the headline numbers reported in the original graduation presentation. The scripts in this repository provide a reproducible route to recalculate supported metrics from the public event data; they are not a byte-for-byte recreation of the original analysis notebook.
Metric	Figure reported in the presentation
Bundesliga points	90
Goals scored	89
Goals conceded	24
Expected goals (xG)	73.6
Pressures	4,786


The presentation also labels Leverkusen's xG as 2nd, goals scored as 2nd, goals conceded as 1st and total pressures as 1st. Those league-wide rankings are reproduced here as source-reported claims, not recalculated by the team-only download script.

The original slides also show player examples including 3,299 passes for Granit Xhaka, 2,167 for Jonathan Tah, 22 through balls for Florian Wirtz, and 13 goals for Alejandro Grimaldo. More source-reported observations are documented in [`docs/ANALYSIS_NOTES.md`](docs/ANALYSIS_NOTES.md).
What the analysis covers
1. Attacking performance
- Season shot map and shot-density view.
- Expected goals and cumulative goals context.
- Attacking locations and final-third activity.
- Player passing and chance-creation indicators.

2. Defensive performance and pressing
- Defensive actions and ball recoveries.
- Pressure locations and pressing activity.
- Pressing patterns in different match states (leading, drawing and trailing).
- Defensive structure and the team's ability to restrict opposition progression.

3. Player performance
The presentation gives individual attention to:
- Florian Wirtz - touch map and pass map.
- Jeremie Frimpong and Alejandro Grimaldo - touch and crossing maps.
- Granit Xhaka and Piero Hincapié - passing activity and distribution.
- Player comparisons involving dribbling and passing volume.

4. Team-level season picture

Tools and technologies
Tool	Use in the project
Python	Data workflow and analysis
pandas	Filtering, cleaning, grouping and aggregation
StatsBomb Open Data / statsbombpy	Match and event data source
Matplotlib	Statistical charts
mplsoccer	Football pitch visualizations
Jupyter Notebook	Exploratory analysis and documentation
