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
