# Urban and Rural Population Analysis in El Jadida (2004-2024)

## Project Overview
This project explores the relationship between urban population growth and built-up area expansion in **El Jadida province, Morocco**, from **2004 to 2024**. By analyzing demographic and spatial data, we aim to understand urbanization trends and their impact on land use.

## Data Sources
The data used in this study comes from two main sources:
1. **Haute Commissariat au Plan (HCP) Morocco** – Official demographic data on urban and rural population percentages.
2. **Satellite Image Analysis (Landsat 8 & ArcGIS)** – Built-up and non-built-up areas were extracted using the **Normalized Difference Built-Up Index (NDBI)**. This was done by processing spectral bands **6** and **5** in ArcGIS. The extracted NDBI values were then reclassified and converted into vector layers to calculate built-up and non-built-up areas in square kilometers.

## Objectives
- Visualize the trend of urbanization over 20 years.
- Analyze the correlation between **urban population percentage** and **built-up area expansion**.
- Calculate the **coefficient of determination (R²)** to quantify the relationship between these two factors.
- Provide insights into land-use changes in El Jadida.

## Methodology
1. **Data Cleaning & Processing**:
   - Demographic data was extracted from HCP reports.
   - Spatial data was processed using Landsat 8 satellite imagery and ArcGIS tools.
   - Percentage values were cleaned and converted for numerical analysis.

2. **Visualization**:
   - Line charts were plotted to compare **urban population growth** and **built-up area expansion** over time.
   - Trends were analyzed to identify periods of rapid urbanization.

3. **Statistical Analysis**:
   - A **linear regression model** was applied to determine the strength of the relationship between urbanization and built-up area expansion.
   - The **R² value** was calculated to measure the correlation.

## Results
- The analysis revealed a **strong correlation (R² ≈ 0.87)** between urban growth and built-up area expansion.
- Over time, as urban population percentages increased, built-up areas also expanded significantly.
- This highlights the ongoing **urbanization process in El Jadida province** and its impact on land use.

## How to Use This Project
1. Download the dataset: `Demographic and Spatial data - Data.csv`
2. Run the Jupyter Notebook `Urban_Population_Analysis.ipynb`
3. View the generated charts and correlation analysis.
4. The final plot can be saved and exported for further reports or presentations.

## Future Improvements
- Integrating **more detailed satellite imagery** to refine built-up area calculations.
- Expanding the study to include additional socio-economic factors.
- Developing predictive models to estimate future urban expansion trends.

## Conclusion
This project provides valuable insights into **urbanization dynamics in El Jadida** over the past two decades. The strong correlation between urban population growth and land-use changes suggests that **urban planning strategies** must consider sustainable development approaches to balance population growth with environmental conservation.


import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score

# Load the dataset
file_path = 'Demographic and Spatial data - Data.csv'  # Ensure the file is in the same directory
df = pd.read_csv(file_path)

# Convert percentage columns to numeric values
for col in ['Non-Build-Up areas (%)', 'Build-Up areas (%)', 'Urban Percentage %', 'Rural Percentage %']:
    df[col] = df[col].str.rstrip('%').astype(float)

df.head()


# Plot the line charts and save as PNG
plt.figure(figsize=(10, 5))
plt.plot(df['Years'], df['Urban Percentage %'], label='Urban Percentage %', marker='o', linestyle='-')
plt.plot(df['Years'], df['Build-Up areas (%)'], label='Build-Up areas %', marker='s', linestyle='--')

plt.xlabel('Years')
plt.ylabel('Percentage (%)')
plt.title('Urban Percentage and Build-Up Area Over the Years')
plt.legend()
plt.grid(True)

plt.savefig("Urban_BuildUp_Chart.png", dpi=300, bbox_inches='tight')  # Save the chart as PNG
plt.show()

# Calculate R² between Urban Percentage and Build-Up Area Percentage
X = df['Build-Up areas (%)'].values.reshape(-1, 1)
y = df['Urban Percentage %'].values

model = LinearRegression()
model.fit(X, y)
y_pred = model.predict(X)
r2 = r2_score(y, y_pred)

print(f'R² Value: {r2:.4f}')

from IPython.display import FileLink

FileLink("Urban_BuildUp_Chart.png")
