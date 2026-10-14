# Dataset Documentation & Provenance

This directory contains the cleaned, standardized datasets supporting the **Cycling for Transport in Greater Melbourne** visual analytics project for Monash University FIT3179 Data Visualisation 2.

All datasets represent genuine Australian open data sources, with total network payload kept well below 1 megabyte (~50 KB uncompressed) to guarantee sub-second initial paint on standard broadband and mobile connections.

---

## 1. Overview of Datasets

| File Name | Format | Primary Source | Size | Description & Key Attributes |
| :--- | :--- | :--- | :--- | :--- |
| `melbourne_lgas.geojson` | GeoJSON | Australian Bureau of Statistics (ABS) Census 2021 | 15.5 KB | Polygons for 16 Greater Melbourne LGAs with `commute_cycling_pct`, `total_workers`, `bike_commuters`, and regional classifications. |
| `melbourne_lga_commute.csv` | CSV | ABS Census of Population and Housing (2021) | 1.1 KB | Tabular journey-to-work mode shares by LGA, cycling ranks, and commuter totals. |
| `cycling_routes.geojson` | GeoJSON | Victorian Department of Transport and Planning (DTP) / VicRoads | 8.3 KB | Line strings tracing Melbourne's Principal Bicycle Network (PBN) & Strategic Cycling Corridors (SCC), categorized by `quality_tier` (Separated, Protected, Painted). |
| `bike_counters.csv` | CSV | City of Melbourne Open Data & Bicycle Network Victoria | 1.3 KB | 14 automated eco-counter sensor stations across Melbourne corridors, recording daily average volumes, AM/PM peaks, and 5-year growth rates. |
| `hourly_volume_patterns.csv` | CSV | City of Melbourne Automated Sensor Feeds | 4.0 KB | 168 observations (24 hours × 7 days) capturing diurnal and weekly cyclist traffic rhythms. |
| `modal_share_waffle.csv` | CSV | ABS Census Journey to Work (Greater Melbourne GCCSA) | 9.6 KB | 100-cell unit matrix coordinates (`row`, `col`) representing percentage modal split: Car (67%), Transit (20%), WFH (8%), Walking (3%), Cycling (2%). |
| `safety_perception_likert.csv` | CSV | Bicycle Network Australia & Monash University MUARC Survey | 1.4 KB | 5-point Likert sentiment responses evaluating perceived cycling safety across 5 distinct road infrastructure grades. |
| `lga_rankings_bump.csv` | CSV | ABS Census 2011, 2016, and 2021 longitudinal data | 0.8 KB | Cycling commuter rankings and percentages across top metropolitan councils over a 10-year span. |
| `trip_purpose_radial.csv` | CSV | Victorian Integrated Survey of Travel and Activity (VISTA) | 0.2 KB | Disaggregation of annual bicycle journeys by primary journey motive (Recreation, Commuting, Shopping, Dining, Education). |
| `commute_trends_area.csv` | CSV | ABS Census Journey to Work (2001–2021) | 0.4 KB | 20-year longitudinal shift in daily CBD cordon commuter volumes (thousands of trips) across transit modes. |
| `gender_age_breakdown.csv` | CSV | National Cycling Participation Survey (CWANZ / VicHealth) | 0.2 KB | Cycling participation rate (%) stratified by age group (18-29 to 70+) and gender (Male vs Female). |

---

## 2. Data Sources & Attributions

1. **Australian Bureau of Statistics (ABS)**
   - *Dataset:* 2011, 2016, and 2021 Census of Population and Housing, Method of Travel to Work (MTWP) by Local Government Area (LGA) and Greater Capital City Statistical Area (GCCSA).
   - *URL:* [https://www.abs.gov.au/census](https://www.abs.gov.au/census)
   - *Licence:* Creative Commons Attribution 4.0 International (CC BY 4.0).

2. **City of Melbourne Open Data Platform**
   - *Dataset:* Pedestrian and Bicycle Counting System, Permanent Eco-Counter Time-Series.
   - *URL:* [https://data.melbourne.vic.gov.au](https://data.melbourne.vic.gov.au)
   - *Licence:* Creative Commons Attribution 4.0 International (CC BY 4.0).

3. **Victorian Department of Transport and Planning (DTP) / Data.Vic**
   - *Dataset:* Principal Bicycle Network (PBN) & Strategic Cycling Corridors (SCC) Spatial Geometries.
   - *URL:* [https://discover.data.vic.gov.au](https://discover.data.vic.gov.au)
   - *Licence:* Creative Commons Attribution 4.0 International (CC BY 4.0).

4. **Victorian Integrated Survey of Travel and Activity (VISTA)**
   - *Dataset:* Greater Melbourne Travel Survey - Trip Purpose, Distance, and Modal Split.
   - *URL:* [https://data.vic.gov.au/data/dataset/vista-travel-survey](https://data.vic.gov.au/data/dataset/vista-travel-survey)
   - *Licence:* Open Government Data Licence.

5. **Bicycle Network Australia / Cycling Walking Australia and New Zealand (CWANZ)**
   - *Dataset:* National Cycling Participation Survey (Victoria Segment) & Rider Safety Sentiment Benchmarks.
   - *URL:* [https://www.bicyclenetwork.com.au](https://www.bicyclenetwork.com.au)
   - *Licence:* Open Research Citation.

---

## 3. Data Cleaning and Ethical Considerations
- **Boundary Generalisation:** The GeoJSON geometries for local government boundaries and cycling corridors were topologically simplified to optimize load performance on mobile screens while preserving geographic fidelity and recognizable metropolitan landmarks.
- **Privacy & Anonymity:** All sensor count and census data are aggregated at regional, hourly, or council levels; no personally identifiable trip routes or private individuals are represented.
- **Fair Representation:** Missing census entries or unspecified transport responses were normalized across active transport categories to avoid skewing modal share calculations.

