# Block Hours Analysis for IndiGo (DEL-BOM Sector)

Analysis of flight On-Time Performance (OTP) for IndiGo's Delhi-Mumbai route using synthetic data. The project calculates block hour overrun, identifies key delay factors, and builds a predictive model for on-time arrivals.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sanjitmathur/Block-Hours-Analysis-for-IndiGo/blob/main/Block_Hours.ipynb)

## Dataset

**File**: `indigo_synthetic_DEL-BOM_last1year.csv` (1,000 flights)

| Column | Description |
|---|---|
| `date`, `flight_number`, `route` | Flight identifiers |
| `aircraft_type` | A320ceo, A320neo, or A321neo |
| `scheduled_block_hours` / `actual_block_hours` | Planned vs actual block time |
| `dep_delay_min` / `arr_delay_min` | Departure and arrival delays (minutes) |
| `otp_arrival_15m` | On-time arrival within 15 min (1 = yes, 0 = no) |
| `weather_index` / `atc_congestion_index` / `wind_component_index` | Environmental factors (0-1 scale) |
| `load_factor`, `pax`, `seats` | Passenger load metrics |
| `fuel_burn_kg`, `fuel_cost_inr_thousands` | Fuel consumption and cost |
| `revenue_inr_thousands` / `profit_inr_thousands` | Financial metrics |

## Analysis

1. **EDA** - Block hour overrun distribution, OTP statistics by delay status
2. **Correlation Analysis** - Feature correlations with OTP target variable
3. **Logistic Regression** - Predicts on-time arrival using overrun, departure delay, aircraft type, weather, and ATC congestion
4. **Visualizations** - Overrun distribution, departure delay box plots, OTP by aircraft type

## Key Results

- **Model Accuracy**: 88%
- **Strongest predictor**: `block_hour_overrun` (coefficient: -8.46)
- **Top delay factors**: Block hour overrun > departure delay > ATC congestion > weather
- Newer aircraft types (A320neo, A321neo) show a slight positive association with OTP

## Requirements

```
pandas
numpy
matplotlib
seaborn
scikit-learn
tabulate
```

## Usage

```bash
pip install pandas numpy matplotlib seaborn scikit-learn tabulate
jupyter notebook Block_Hours.ipynb
```
