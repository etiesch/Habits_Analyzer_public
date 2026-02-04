# Habits Analyzer

A comprehensive data analysis tool for tracking and visualizing personal habits using data exported from the [uHabits](https://github.com/iSoron/uhabits) mobile application.

![dendrogram](dendrogram.png)

## Overview

This project analyzes habit tracking data with the following capabilities:

- **Data Normalization**: Converts uHabits app data into a standardized format
- **Temporal Analysis**: Organizes and aggregates data by months and years
- **Multiple Visualizations**: Yearly summaries, monthly reports, and calendar heatmaps
- **Statistical Analysis**: Computes correlations between habits and performs hierarchical clustering
- **Metric Tracking**: Includes analysis of numeric data like weight and sleep duration

## Features

### 1. **Yearly Reports**
   - Comprehensive summaries of all tracked habits organized by year
   - Individual habit progress charts with cumulative days
   - Weight and sleep duration trends over the year

### 2. **Monthly Reports**
   - Detailed monthly breakdowns by activity category
   - Month-over-month comparisons with scoring
   - Separate analysis for weight and sleep metrics

### 3. **Calendar Views**
   - Interactive calendar heatmaps showing daily activity levels
   - One calendar per habit for easy pattern recognition
   - Color-coded intensity visualization

### 4. **Correlation Analysis**
   - Heatmap showing correlations between all tracked habits
   - Identification of top positive and negative correlations
   - Hierarchical clustering dendrogram for habit grouping

## Requirements

- Python 3.7+
- pandas
- numpy
- matplotlib
- seaborn
- scipy
- calplot

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/Habits-Analyzer.git
cd Habits-Analyzer
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Set Up Jupyter (if not already installed)

**Option A: Command Line**
```bash
pip install jupyter
```

**Option B: Visual Studio Code**
- Install [VS Code](https://code.visualstudio.com/download)
- Install the Python extension for VS Code
- The Jupyter extension will be suggested automatically

## Usage

### 1. Export Data from uHabits

Export your habit data from the uHabits app:
- **PlayStore**: https://play.google.com/store/apps/details?id=org.isoron.uhabits
- **F-Droid**: https://f-droid.org/packages/org.isoron.uhabits/
- **GitHub**: https://github.com/iSoron/uhabits

### 2. Prepare Your Data

Place the exported CSV file (`Checkmarks.csv`) in the project root directory.

### 3. Configure Analysis Options

Open `Habits Analysis.ipynb` and modify the options cell:

```python
option_plot_yearly = True           # Generate yearly summaries
option_plot_monthly = True          # Generate monthly reports
option_plot_calendar_view = True    # Generate calendar heatmaps

# Categorize activities by keyword (case-insensitive)
list_of_activities_to_separate = ["Activité", "Mood", "Ordi", "Photos", "Taf", "Repas", "Sommeil"]
```

### 4. Run the Analysis

**Option 1: Command Line**
```bash
jupyter notebook
```
Then select `Habits Analysis.ipynb` and run all cells.

**Option 2: Visual Studio Code**
- Open the folder in VS Code
- Click on `Habits Analysis.ipynb`
- Click "Run All" or run cells individually

## Data Format

The input CSV file should contain:
- **Date**: Date of the entry (YYYY-MM-DD format)
- **Activity columns**: One column per tracked habit
- **Poids**: Weight measurements
- **Durée sommeil**: Sleep duration

### Value Encoding

- `2`: Habit completed (checked)
- `1`, `0`: Habit not completed (unchecked)
- `-1`: Missing value (converted to NaN)

## Output

The analysis generates:

1. **Yearly Summaries**: Weight/sleep trends + monthly habit aggregates
2. **Monthly Reports**: Month-over-month comparisons with scoring
3. **Calendar Heatmaps**: Daily intensity visualization for each habit
4. **Statistical Analysis**: Correlation heatmaps and clustering dendrograms

## Customization

### Activity Categories

Modify `list_of_activities_to_separate` to match your habit naming:
```python
list_of_activities_to_separate = ["Your", "Categories", "Here"]
```

### Color Schemes

- Bar charts: Modify `sns.color_palette("Dark2")`
- Calendar heatmaps: Modify `color_palette_list` variable

### Time Range

Exclude specific years:
```python
df = df[df["Date"].dt.year != 2023]  # Remove or modify
```

## Project Structure

```
Habits-Analyzer/
├── README.md                      # This file
├── Habits Analysis.ipynb          # Main analysis notebook
├── Checkmarks.csv                 # Input data (from uHabits app)
└── requirements.txt               # Python dependencies

```

## Troubleshooting

| Issue | Solution |
|-------|----------|
| `ModuleNotFoundError` | Run `pip install -r requirements.txt` |
| `FileNotFoundError: Checkmarks.csv` | Ensure CSV is in project root directory |
| Plots not displaying | Use Jupyter notebook or VS Code with Jupyter support |
| Data not loading | Check CSV file format and column names |


This project is open source and available under the MIT License.

---

**Note**: This project is designed for personal habit tracking. Ensure you have permission to export and analyze your own data. The data provided in Checkmarks.csv are randomized.
