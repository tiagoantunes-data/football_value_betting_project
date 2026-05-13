# Premier League Goals Probability Model

A statistical model using **Poisson distribution** to estimate goal probabilities in Premier League matches. Model-implied probabilities are compared against Bet365 market odds and validated against actual match outcomes across a full season.

---

## Methodology

1. **Data Loading** — Full Premier League 2024/25 season results and Bet365 Over 2.5 odds from [football-data.co.uk](https://www.football-data.co.uk/)
2. **Team Strength Estimation** — Calculate attack and defence indices for each team relative to the league average
3. **Expected Goals** — Estimate λ (expected goals) per team using strength indices
4. **Poisson Distribution** — Derive goal probability distributions and compute Over 2.5 probability
5. **Backtesting** — Apply model to all 380 matches and validate against actual results and market odds

---

## Project Structure

```
football_analysis_project/
├── data/
│   └── premier_league_2024_25.csv    # Match results + Bet365 odds
├── football_analysis_project.ipynb   # Main analysis notebook
├── requirements.txt                   # Python dependencies
├── LICENSE
├── .gitignore
└── README.md
```

---

## Tech Stack

- **Python 3.10+**
- Pandas — data manipulation
- NumPy — numerical operations
- SciPy — Poisson distribution
- Matplotlib — visualisations

---

## Setup

### 1. Clone the repository

```bash
git clone <repo-url>
cd football_analysis_project
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the notebook

```bash
jupyter notebook football_analysis_project.ipynb
```

No API keys or environment variables required.

---

## Results Preview

Sample output — top 10 matches by model-market divergence (2024/25 season):

| Home | Away | Probability | Model Odds | Market Odds | Divergence | Actual |
|---|---|---|---|---|---|---|
| Fulham | Bournemouth | 68.5% | 1.46 | 1.57 | +0.11 | Over |
| Tottenham | Leeds Utd | 57.7% | 1.73 | 1.81 | +0.08 | — |
| Man United | Nott'm Forest | 63.0% | 1.59 | 1.66 | +0.07 | Over |
| Arsenal | Burnley | 78.9% | 1.27 | 1.33 | +0.06 | Over |
| Crystal Palace | Everton | 25.2% | 3.97 | 2.06 | -1.91 | Under |

---

## Key Outputs

- Goal scoring distribution across the full Premier League season
- Team attack and defence strength indices
- Model-implied vs market-implied odds for all 380 matches
- Calibration chart: predicted probability buckets vs actual over 2.5 rate
- Backtesting accuracy by divergence direction

---

## Model Limitations

- Poisson distribution assumes goal independence between home and away teams
- Full-season averages do not weight recent form
- No contextual features (injuries, suspensions, match importance)
- Backtesting uses the same season for training and evaluation — a proper out-of-sample test would train on a prior season

---

## Potential Extensions

- Out-of-sample backtesting (train on 2023/24, test on 2024/25)
- Expected Goals (xG) as input instead of raw goals
- Recency weighting for team strength estimates
- Machine learning to incorporate contextual features
- Additional markets: match result (1X2), Both Teams to Score

---

## Skills Demonstrated

- Statistical modelling (Poisson distribution)
- Data loading, cleaning, and transformation
- Exploratory data analysis and visualisation
- Model calibration and backtesting
- Probability theory applied to sports analytics
