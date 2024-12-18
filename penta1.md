

# Penta1 Coverage Analysis with Python

## Prerequisites

### Install Necessary Libraries
Before running the script, install the following Python libraries:
```bash
pip install pandas numpy geopandas matplotlib
```

---

## Step-by-Step Explanation of the Code

### Step 1: Import Libraries
```python
import pandas as pd
import numpy as np
import geopandas as gpd
import matplotlib.pyplot as plt
from functools import reduce
from matplotlib.colors import BoundaryNorm
```
This step imports essential libraries for data manipulation (`pandas`, `numpy`), geospatial analysis (`geopandas`), and visualization (`matplotlib`).

### Step 2: Read the Input Files
```python
shapefile = gpd.read_file('/content/Chiefdom 2021.shp')
df = pd.read_excel('intervention_data_new (1).xlsx')
df_population = pd.read_excel('/content/pop_chie_data.xlsx')
```
The code reads:
1. A shapefile for geospatial boundaries.
2. Excel files containing intervention data and population data.

### Step 3: Filter Rows and Group by Year
```python
dfs = []
for year in range(2015, 2024):
    df_year = df[df['year'] == year]
    df_grouped = df_year.groupby(['adm1', 'adm2', 'adm3'], as_index=False)['penta1_tot'].sum()
    df_grouped = df_grouped.rename(columns={'penta1_tot': f'penta1_{year}'})
    dfs.append(df_grouped)
```
This step:
- Filters data for each year.
- Groups rows by administrative levels and sums `penta1_tot`.
- Stores results in a list of DataFrames.

### Step 4: Merge Grouped DataFrames
```python
df_merge = reduce(lambda left, right: pd.merge(left, right, on=['adm1', 'adm2', 'adm3'], how='outer'), dfs)
```
Combines all yearly DataFrames into a single DataFrame using an outer join.

### Step 5: Merge with Population Data
```python
combined_data = df_merge.merge(df_population, on='adm3', how='left')
```
Joins the merged yearly data with population data.

### Step 6: Merge with Shapefile
```python
data = shapefile.merge(combined_data, on=['FIRST_DNAM', 'FIRST_CHIE'], how='left')
```
Combines shapefile data with the analysis dataset for geospatial visualization.

### Step 7: Calculate Penta1 Coverage
```python
for year in range(2015, 2024):
    data[f'penta1_coverage_{year}'] = (
        (data[f'penta1_{year}'] / (data[f'pop{year}'] * 0.037)) * 100
    ).round(2)
```
Calculates Penta1 coverage percentage for each year, rounding to two decimal places.

### Step 8: Define Colormap
```python
years = list(range(2015, 2024))
cmap = plt.cm.Blues
bounds = [0, 20, 40, 60, 80, 100]
norm = BoundaryNorm(bounds, ncolors=cmap.N, clip=True)
```
Sets the color scheme and normalization for coverage visualization.

### Step 9: Create Yearly Plots
```python
for year in years:
    fig, ax = plt.subplots(figsize=(8, 6))
    column_name = f"penta1_coverage_{year}"
    data.plot(column=column_name, cmap=cmap, norm=norm, edgecolor="black", linewidth=0.5, legend=False, ax=ax)
    ax.set_title(f"Penta1 Coverage {year}", fontsize=14, fontweight="bold")
    ax.axis("off")
    sm = plt.cm.ScalarMappable(cmap=cmap, norm=norm)
    sm._A = []
    cbar = fig.colorbar(sm, ax=ax, orientation="vertical", fraction=0.03, pad=0.02)
    cbar.set_label("Coverage (%)", fontsize=12)
    output_file = f"penta1_{year}.png"
    plt.savefig(output_file, dpi=300, bbox_inches="tight")
    print(f"Figure saved as {output_file}")
    plt.show()
    plt.close(fig)
```
For each year:
- Creates a map visualization.
- Saves the plot as a PNG file.
- Displays and closes the plot.

---

## Full Code
```python
import pandas as pd
import numpy as np
import geopandas as gpd
import matplotlib.pyplot as plt
from functools import reduce
from matplotlib.colors import BoundaryNorm

shapefile = gpd.read_file('/content/Chiefdom 2021.shp')
df = pd.read_excel('intervention_data_new (1).xlsx')
df_population = pd.read_excel('/content/pop_chie_data.xlsx')

dfs = []
for year in range(2015, 2024):
    df_year = df[df['year'] == year]
    df_grouped = df_year.groupby(['adm1', 'adm2', 'adm3'], as_index=False)['penta1_tot'].sum()
    df_grouped = df_grouped.rename(columns={'penta1_tot': f'penta1_{year}'})
    dfs.append(df_grouped)

df_merge = reduce(lambda left, right: pd.merge(left, right, on=['adm1', 'adm2', 'adm3'], how='outer'), dfs)
combined_data = df_merge.merge(df_population, on='adm3', how='left')
data = shapefile.merge(combined_data, on=['FIRST_DNAM', 'FIRST_CHIE'], how='left')

for year in range(2015, 2024):
    data[f'penta1_coverage_{year}'] = (
        (data[f'penta1_{year}'] / (data[f'pop{year}'] * 0.037)) * 100
    ).round(2)

years = list(range(2015, 2024))
cmap = plt.cm.Blues
bounds = [0, 20, 40, 60, 80, 100]
norm = BoundaryNorm(bounds, ncolors=cmap.N, clip=True)

for year in years:
    fig, ax = plt.subplots(figsize=(8, 6))
    column_name = f"penta1_coverage_{year}"
    data.plot(column=column_name, cmap=cmap, norm=norm, edgecolor="black", linewidth=0.5, legend=False, ax=ax)
    ax.set_title(f"Penta1 Coverage {year}", fontsize=14, fontweight="bold")
    ax.axis("off")
    sm = plt.cm.ScalarMappable(cmap=cmap, norm=norm)
    sm._A = []
    cbar = fig.colorbar(sm, ax=ax, orientation="vertical", fraction=0.03, pad=0.02)
    cbar.set_label("Coverage (%)", fontsize=12)
    output_file = f"penta1_{year}.png"
    plt.savefig(output_file, dpi=300, bbox_inches="tight")
    print(f"Figure saved as {output_file}")
    plt.show()
    plt.close(fig)
```

---

## Output
