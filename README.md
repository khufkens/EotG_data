```diff
! The formal release of this work can now be found on the Radiant Earth ML hub
```

# Eyes on the Ground STAC data catalogue (v1)

The "Eyes on the Ground" project ([lacunafund.org](lacunafund.org)) is a collaboration between ACRE Africa, the International Food Policy Research Institute (IFPRI), and the Lacuna Fund, to create a large machine learning (ML) dataset of smallholder farmer's fields based upon previous work within the Picture Based Insurance framework (Ceballos, Kramer and Robles, 2019, [https://doi.org/10.1016/j.deveng.2019.100042](https://doi.org/10.1016/j.deveng.2019.100042)). This is a unique dataset of georeferenced crop images along with labels on input use, crop management, phenology, crop damage, and yields, collected across 8 counties in Kenya. The research leading to this dataset was undertaken as part of the CGIAR research program on Policies, Institutions and Markets (PIM)

Data are anonymized by only providing regional bounding boxes. Their geo-spatial component is therefore explicitly regional. However, to provide opportunities for making links to remote sensing data and using the data in a more varied way we provide a number of ancillary data sets extracted at point locations for farmer fields.

Overall we provide:

- 28K curated crop images for machine learning (of which this is part 1, or roughly 16K images)
- crop damage labels, either manually provided or automatically determined
- Sentinel 2 data to calculate vegetation indices
- ARC and TAMSAT precipitation estimates
- ERA5 climate variables (limited to 09/07/2021)

To browse the data visually visit the data repository in the **[Radiant Earth ML hub](https://mlhub.earth/data/lacuna_fund_eotg_v1)**.

# Labelled and curated images

All images have been manually curated and to a large extend have been labelled for crop development phase (phenology), and weather related disturbances. In absence of such labels we used an in house machine learning algorithm to label development stages and disturbance probabilities. However, the ML algorithm might be still improved upon so this dataset serves as a reference for such work.

Machine Learning labels provided consist of:

## manual labels (json label)

- growth stage (growth_stage)
- damage type (damage)
- damage extent (extent)

## ML labels (json label)

- drought probability (drought_probability)
- drought extent (drought_extent)
- sowing phase (growth_sowing)
- vegetative phase (growth_vegetative)
- flowering phase (growth_flowering)
- maturity phase (growth_maturity)
- no disturbance probability (disturbance_none)
- weed disturbance (disturbance_weed)
- drought disturbance (disturbance_drought)
- nutrient deficit (disturbance_nutrient_deficit)

# Ancillary data

## Sentinel 2 data

Sentinel 2 data is provided as raw band values an quality control labels, in particular bands: B1, B2, B3, B4, B8, AOT, SCL, QA60 (as listed on [Google Earth Engine](https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2)). These data were extracted using the pypi gee_subset package.

## ERA 5 data

Similar to Sentinel 2 data daily aggregates of climate variables were extracted from Google Earth Engine spanning the 2020 - 2021 time frame. However, the data is currently truncated at 09/07/2021 due to a slow release cycle of the daily values. In the dataset the following variables are included:

- Surface pressure
- 2m mean air temperature
- 2m minimum air temperature
- 2m maximum air temperature
- 2m dewpoint temperature
- total precipitation
- mean sea level pressure
- u and v components of wind

For units we refer to the source data on the [Google Earth Engine catalogue](https://developers.google.com/earth-engine/datasets/catalog/ECMWF_ERA5_DAILY).

## ARC and TAMSAT precipitation climatology data

We provide daily precipitation estimates as extracted from two remote sensing products. We use both [TAMSAT](https://www.tamsat.org.uk/), where "TAMSAT produces daily rainfall estimates for all of Africa at 4km resolution." In addition, daily precipitation values are provided through [ARC2 data](http://iridl.ldeo.columbia.edu/SOURCES/.NOAA/.NCEP/.CPC/.FEWS/.Africa/.DAILY/.ARC2/.daily/) as provided by NOAA. Data are extracted at point locations, for units we refer to the product websites.

