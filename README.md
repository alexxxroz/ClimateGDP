# ClimateGDP

The project was made as part as the Big Data Infastructure and Technologies course in ITMO University.

**Aim**: to develop ML models to estimate GDPs of 34 European countries using meteorological and agricultural data.

**Predictors**:
- 2 m air temperature (t2m; ERA5 on single level);
- total precipitations (tp; ERA5 on single level);
- agricultural land area (agr; The World Bank);
- cereal yield (yld; The World Bank).

**Target**:
- gross domestic product (gdp; The World Bank).

**1st Stage.**
According to a list of European countries all names were unified to one notation before data agreggation. Aftewards, the economy data were processed with drop out of states with NAN values.
To gather climate data with spatial resolution of 0.25° it was necessary to slice the data accroding to the official borders (*.shp* file comprises this information) and average hourly data over years with following aggregation.

![cluster_map](https://github.com/alexxxroz/ClimateGDP/assets/107231688/353ad9cb-792b-469d-a4b5-a8e2d023f9cb)

**2d Statge.**
On this stage a k-means clustering was applied to split the countries on some groups (it was decided to have 3). Then heatmaps, lineplots and scatterpots were created to investigate the collected data.

![kmeans_clustering](https://github.com/alexxxroz/ClimateGDP/assets/107231688/6e5c3f0a-2055-44c5-b7e4-12237a5973a8)


**3d Stage.**
To prove that meteorological data have an impact on GDP two datasets were obtained. Finally, XGBoost and RF models were built and trained with flollowing evaluation (R^2). For the best model (XGBoost) a sensetivity analysis was applied to see how the std of meteo variables can change the output of the model using Monte-Carlo technique.

![t2m_mape](https://github.com/alexxxroz/ClimateGDP/assets/107231688/6efc30a9-29af-4c8e-a95c-ed35b8cfcb1c)
![tp_mape](https://github.com/alexxxroz/ClimateGDP/assets/107231688/65e852de-8c1e-433a-b810-471effe3ba3b)


**Conclusions:**
1. GDPs of 34 European countries were successfully modelled using two ML algortithms + k-means clustering and evaluated;
2. Climate (2 m air temperature and total precipitations) is one of the key components for well-being of all, even post-industrial economies;
3. It’s possible to forecast GDPs of European countries using different warming scenarios to lead a proper decision-making policy.
