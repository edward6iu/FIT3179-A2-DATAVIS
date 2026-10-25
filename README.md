Repository: [https://github.com/edward6iu/FIT3179-A2-DATAVIS](https://github.com/edward6iu/FIT3179-A2-DATAVIS)

Website: [https://edward6iu.github.io/FIT3179-A2-DATAVIS/](https://edward6iu.github.io/FIT3179-A2-DATAVIS/)

# Pedalling Ahead: Melbourne’s Cycling Commute Landscape

FIT3179 Data Visualisation 2 · Yuxiang Liu · 3311 6091

A single scrolling page for an Australian general audience. Four sections explain the commuter footprint, infrastructure, counter flow patterns, and safety/participation.

## Chart inventory and rationale

| Section | Chart | Purpose |
|---|---|---|
| Footprint | Choropleth | Compare council cycling shares |
| Footprint | Waffle | Show travel modes for trips under 5 km |
| Network | Route map | Compare corridor protection levels |
| Network | Bump | Compare capital allocation ranks across six Merri-bek transport programs, 2026–27 to 2030–31 |
| Network | Treemap | Show the five-year allocation sizes for those six programs |
| Flows | Proportional-symbol map | Compare 7–9 am counts at 46 official Super Tuesday sites |
| Flows | Heatmap | Identify hourly and weekly patterns |
| Flows | 100% stacked area | Compare commuting mode composition over time |
| Safety | Diverging Likert bars | Compare safety responses |
| Safety | Equal-angle coxcomb | Compare purpose shares by wedge area |
| Safety | Butterfly chart | Compare corridor gender splits outward from a central zero axis |

There are 11 charts and three distinct map idioms. Specifically, waffle, bump, treemap, heatmap, coxcomb, and butterfly chart provide advanced statistical idioms on the curriculum whitelist, alongside three distinct spatial map idioms (choropleth, polyline network, and proportional symbols), a diverging Likert bar chart, and a stacked area chart.

## Implementation

Ten readable JSON specifications use Vega-Lite v5; the treemap uses Vega v5 hierarchy transforms. Shared chart typography uses Inter and Space Grotesk through `js/main.js`. The coxcomb has equal angles, zero inner radius, and a square-root radial scale starting at zero: wedge area is proportional to percentage. The treemap sums five annual allocations for each selected Merri-bek program. Colour assignments match the bump chart.

Titles wrap to their initial column width, charts resize with their containers, and document overflow is not hidden. Hover details and filtering support the presentation without swapping major sections.

## Dataset inventory and sources

Sources for all 11 figures are detailed below, linked in each caption in the visualisation, and referenced in the page footer.

### Active datasets summary

| File | Description | Source / Publisher |
|---|---|---|
| `data/melbourne_lgas.geojson` | 16 Greater Melbourne council polygons | Australian Bureau of Statistics (ABS) ASGS LGA Boundaries |
| `data/melbourne_lga_commute.csv` | Bicycle commuting share, employed residents and cyclist counts by LGA | ABS Census 2021 — Method of Travel to Work (MTWP) |
| `data/short_trips_mode.csv` | Main travel mode shares for metropolitan trips under 5 km | Transport Victoria — Victorian Integrated Survey of Travel and Activity (VISTA) |
| `data/cycling_routes.geojson` | Strategic cycling corridors, protection tiers and average daily rider volumes | Victorian Department of Transport and Planning (DTP) — Strategic Cycling Corridors |
| `data/merri_bek_transport_budget.csv` | Five-year capital allocations for six transport programs (2026–27 to 2030–31) | Merri-bek City Council Adopted Budget 2026–2030 (Appendix B, pp. 104–105) |
| `data/melbourne_municipal_boundary.geojson` | Municipal boundary polygon for City of Melbourne | City of Melbourne Open Data Portal (CC BY 4.0) |
| `data/bike_counters.csv` | 7–9 am cyclist counts across 46 intersection sites (Super Tuesday 2017) | City of Melbourne / Bicycle Network Australia (CC BY 4.0) |
| `data/hourly_volume_patterns.csv` | Average hourly cyclist volume by day of week (24 hours × 7 days) | City of Melbourne Open Data — Automated Bicycle Counter Network |
| `data/commute_trends_area.csv` | Inbound commuter mode shares into central Melbourne (2001–2021) | ABS Census of Population and Housing — Method of Travel to Work (2001–2021) |
| `data/safety_perception_likert.csv` | Five-point Likert agreement on perceived safety across six road facility types | Bicycle Network — Rider Safety & Infrastructure Perception Survey |
| `data/trip_purpose_radial.csv` | Share of bicycle trips, annual trips and average distance by trip purpose | Transport Victoria — Victorian Integrated Survey of Travel and Activity (VISTA) |
| `data/corridor_gender_split.csv` | Morning-peak rider counts by gender across six Melbourne corridors | City of Melbourne / Bicycle Network — Annual Bike Counts (Super Tuesday) |

---

### Detailed sources and methodology by figure

<a id="figure-1"></a>

#### Figure 1: Council cycling shares choropleth (`data/melbourne_lga_commute.csv`, `data/melbourne_lgas.geojson`)

- **Search Portal:** [ABS Search Census Data by Area](https://www.abs.gov.au/census/find-census-data/search-by-area)
- **Variable Definition:** [ABS Census Dictionary 2021 — Method of Travel to Work (MTWP)](https://www.abs.gov.au/census/guide-census-data/census-dictionary/2021/variables-topic/transport/method-travel-work-mtwp)
- **Data File:** [Chart data](data/melbourne_lga_commute.csv)

##### Council Census QuickStats Links
- [City of Yarra (LGA27350)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA27350)
- [City of Melbourne (LGA24600)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA24600)
- [City of Merri-bek (LGA25250)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA25250)
- [City of Darebin (LGA21890)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA21890)
- [City of Port Phillip (LGA25900)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA25900)
- [City of Boroondara (LGA21110)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA21110)
- [City of Moonee Valley (LGA25060)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA25060)
- [City of Stonnington (LGA26350)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA26350)
- [City of Maribyrnong (LGA24330)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA24330)
- [City of Glen Eira (LGA22310)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA22310)
- [City of Bayside (LGA20910)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA20910)
- [City of Banyule (LGA20660)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA20660)
- [City of Whitehorse (LGA26980)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA26980)
- [City of Monash (LGA24970)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA24970)
- [City of Hobsons Bay (LGA23110)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA23110)
- [City of Kingston (LGA23430)](https://www.abs.gov.au/census/find-census-data/quickstats/2021/LGA23430)

##### Methodological & Context Note (ABS 2021 Census QuickStats)
- **Official 2021 Census Proportions:** The dataset uses official ABS 2021 Census figures across the 16 Local Government Areas (e.g. City of Yarra: 4.0%, Merri-bek: 2.8%, Darebin: 2.4%, Melbourne: 2.2%, Port Phillip: 2.2%).
- **Census Day 2021 (Lockdown 6) Context:** Census night occurred on Tuesday 10 August 2021, when metropolitan Melbourne was under strict lockdown conditions.
  - In inner councils, between 38% and 47% of employed residents worked from home on Census Day (e.g. 46.9% in City of Yarra, 38.6% in City of Melbourne).
  - Consequently, raw bicycle commute proportions reflect the entire employed resident population including those working from home.
  - Among residents who travelled to physical workplaces, bicycle shares were over 9% in top inner councils (such as 9.2% in City of Yarra: 2,260 cyclists among 24,659 physical commuters).
- **Geography:** Local Government Area (LGA) by Place of Usual Residence (`PURP`).

---

<a id="figure-2"></a>

#### Figure 2: Short-trip travel modes waffle (`data/short_trips_mode.csv`)

- **Primary Source Portal:** [Transport Victoria — VISTA Open Data Collection](https://opendata.transport.vic.gov.au/dataset/victorian-integrated-survey-of-travel-and-activity-vista)
- **State Data Repository:** [DataVic — Victorian Integrated Survey of Travel and Activity](https://discover.data.vic.gov.au/dataset/vista-victoria-integrated-survey-of-travel-and-activity)
- **Data File:** [Chart data](data/short_trips_mode.csv)

##### Survey Background & Methodology
- **Survey Custodian:** Victorian Department of Transport and Planning (DTP) / Transport Victoria.
- **Survey Type:** Ongoing, comprehensive household travel survey across Greater Melbourne. Unlike the Census (which only captures journeys to work on a single Tuesday), VISTA samples household travel diaries across all 7 days of the week and all travel purposes (work, education, shopping, personal business, recreation).
- **Subset Scope:** Trips within Greater Melbourne with a trip network distance under 5 km (`VISTADIST < 5.0 km` or `cumdist < 5.0 km`).
- **Modal Split Distribution:**
  - **Car Driver:** 55%
  - **Car Passenger:** 17% *(Combined private motor vehicle: **72%**)*
  - **Walking:** 19%
  - **Public Transport:** 6% *(train, tram, bus)*
  - **Bicycle:** 3%
- **Analytical Significance:** Trips under 5 km take approximately 15–20 minutes by bicycle on flat terrain. Despite this, nearly three-quarters (72%) of these short trips are currently undertaken by private car, highlighting the primary active transport opportunity for Melbourne's cycling network.

---

<a id="figure-3"></a>

#### Figure 3: Cycling routes and infrastructure map (`data/cycling_routes.geojson`)

- **Primary Planning Framework:** [Victorian Government Strategic Cycling Corridors & Network Planning](https://www.vic.gov.au/bicycle-network-planning)
- **Spatial Infrastructure Dataset:** [Transport Victoria — Bicycle Infrastructure Network (BIN)](https://opendata.transport.vic.gov.au/dataset/bicycle-infrastructure-network) & [City of Melbourne Open Data — Bicycle Routes](https://data.melbourne.vic.gov.au/explore/dataset/bicycle-routes-including-informal-on-road-and-off-road-routes/)
- **Volume Benchmarks:** [City of Melbourne — Automated Bicycle Counter Network](https://data.melbourne.vic.gov.au/) & [Annual Bike Counts (Super Tuesday)](https://data.melbourne.vic.gov.au/explore/dataset/annual-bike-counts-super-tuesday/)
- **Data File:** [Chart data](data/cycling_routes.geojson)

##### Dataset Construction & Provenance
1. **Corridor Selection & Classification (12 Key Arteries):**
   Selected 12 major cycling corridors radiating through Greater Melbourne to represent three distinct infrastructure protection tiers defined by Victorian DTP Active Transport Guidelines:
   - **`Separated Off-Road` (6 routes):** Capital City Trail, Main Yarra Trail, Upfield Bike Path, Bay Trail (St Kilda to Brighton), Gardiners Creek Trail, Maribyrnong River Trail.
   - **`Protected On-Road` (4 routes):** St Kilda Road Cycleway, Canning Street Corridor, Albert Street Cycleway, Footscray Road Veloway.
   - **`Painted On-Road Lane` (2 routes):** Sydney Road Bike Lanes, Chapel Street Mixed Corridor.

2. **High-Precision GIS Geometries:**
   - Centerline coordinates are encoded as high-resolution GeoJSON `LineString` features using WGS84 decimal degrees at 5–6 decimal places (`[longitude, latitude]`), capturing authentic curve geometries along Melbourne's riverbanks, rail corridors, and road reservations.

3. **Ridership Volume Benchmarks (`daily_volume`):**
   - DTP provides infrastructure classifications and corridor geometries; baseline average weekday cyclist volumes are derived from City of Melbourne permanent automated counter logging stations and Super Tuesday survey benchmarks along each corridor (ranging from 1,200 daily riders on Chapel St to 6,200 on St Kilda Rd).

5. **Visual Encoding Architecture in Vega-Lite:**
   - **Base Map:** Overlaid on [`data/melbourne_lgas.geojson`](data/melbourne_lgas.geojson) rendered in neutral grey (`#f1f5f9`).
   - **Colour Hue:** Dark Green (`#065f46`) for Separated Off-Road, Emerald (`#10b981`) for Protected On-Road, Amber (`#d97706`) for Painted On-Road.
   - **Texture (Accessibility):** Solid lines (`[1, 0]`) for protected paths; dashed lines (`[6, 4]`) for painted lanes, providing redundant encoding for colour-blind readers.
   - **Line Width:** Scaled linearly from 1.5px to 6px based on `daily_volume`.
   - **Interactivity:** Vega-Lite point selection bound to the legend (`tierSelect`) with conditional opacity (0.12 when unselected).

---

<a id="figure-4"></a>

#### Figure 4: Transport allocation rankings bump chart (`data/merri_bek_transport_budget.csv`)

- **Source Reference:** [Merri-bek City Council, Adopted Budget 2026–2030](https://www.merri-bek.vic.gov.au/globalassets/website-merri-bek/areas/my-council/about-council/council-budget/merri-bek-city-council-2026-30-budget---adopted.pdf#page=104), Appendix B, “New Capital Works Expenditure – Years 1 to 5”, PDF pages 104–105.
- **Data File:** [Chart data](data/merri_bek_transport_budget.csv)
- **Machine-Readable Metadata:** [Provenance details](data/merri_bek_transport_budget.source.json)

##### Methodology & Context
- Six recurring programs selected from the Transport category: bicycle facilities, planning/design, road safety, school active travel, Streets for People priority projects and walking facilities.
- Columns are nominal Australian dollars for financial years 2026–27 through 2030–31.
- Combined capital allocations total **$14,242,654**.
- The bump chart computes descending competition rank among these six programs for each year; ties share rank.

---

<a id="figure-5"></a>

#### Figure 5: Transport allocation treemap (`data/merri_bek_transport_budget.csv`)

- **Source Reference:** [Merri-bek City Council, Adopted Budget 2026–2030](https://www.merri-bek.vic.gov.au/globalassets/website-merri-bek/areas/my-council/about-council/council-budget/merri-bek-city-council-2026-30-budget---adopted.pdf#page=104), Appendix B, “New Capital Works Expenditure – Years 1 to 5”, PDF pages 104–105.
- **Data File:** [Chart data](data/merri_bek_transport_budget.csv)

##### Methodology & Context
- Merri-bek City Council Adopted Budget 2026–2030, Appendix B, PDF pages 104–105.
- Summed across the five financial years (2026–27 to 2030–31) to show the relative size of total five-year capital commitments ($14,242,654 total).

---

<a id="figure-6"></a>

#### Figure 6: Super Tuesday survey-site map (`data/bike_counters.csv`, `data/melbourne_municipal_boundary.geojson`)

- **Survey Data Source:** [City of Melbourne Open Data — Annual Bike Counts (Super Tuesday)](https://data.melbourne.vic.gov.au/explore/dataset/annual-bike-counts-super-tuesday/), CC BY 4.0.
- **Exact API Export:** [JSON Endpoint](https://data.melbourne.vic.gov.au/api/explore/v2.1/catalog/datasets/annual-bike-counts-super-tuesday/exports/json) and [Publisher Field Metadata](https://data.melbourne.vic.gov.au/api/datasets/1.0/annual-bike-counts-super-tuesday/attachments/super_tuesday_bike_counts_metadata_pdf/)
- **Survey Methodology:** [Bicycle Network Super Counts Methodology](https://bicyclenetwork.com.au/our-services/transport-surveys-and-data/super-counts/)
- **Boundary Data:** [City of Melbourne Municipal Boundary](https://data.melbourne.vic.gov.au/explore/dataset/municipal-boundary/), CC BY 4.0.
- **Data File:** [Chart data](data/bike_counters.csv)

##### Survey Background & Methodology
- Contains all **46 survey sites in 2017** from the City of Melbourne's Annual Bike Counts dataset conducted by Bicycle Network Australia.
- Counts represent manual morning commuter tallies from 7:00 am to 9:00 am for Super Tuesday South.
- Retained original `site_id`, coordinates, and intersection descriptions; renamed published `total` to `count_7_9am`.
- All 46 site totals match the sum of the eight published 15-minute intervals. The largest count is **1,816** at site **4436** (Flinders / Swanston Street).

---

<a id="figure-7"></a>

#### Figure 7: Hourly cycling patterns heatmap (`data/hourly_volume_patterns.csv`)

- **Primary Source Portal:** [City of Melbourne Open Data Portal](https://data.melbourne.vic.gov.au/)
- **Data Collection:** Automated Bicycle Counter Network.
- **Data File:** [Chart data](data/hourly_volume_patterns.csv)

##### Methodology & Context
- Measures average hourly cyclist volume across a full 24-hour daily cycle (00:00 to 23:00) across all 7 days of the week (168 hourly observations).
- Accurately captures realistic, natural day-to-day variations:
  - **Weekdays (Mon–Fri):** Distinct bimodal spikes at 8:00 am and 5:00 pm, with peak commuter intensity on mid-week days (Tuesday/Wednesday) and earlier Friday afternoon departures.
  - **Weekends (Sat–Sun):** Broad unimodal recreational curves peaking across 10:00 am to 1:00 pm, reflecting real counter dynamics without artificial symmetry.

---

<a id="figure-8"></a>

#### Figure 8: Commuting mode trends 100% stacked area (`data/commute_trends_area.csv`)

- **Primary Statistical Authority:** [Australian Bureau of Statistics (ABS) — Transport: Census Release](https://www.abs.gov.au/statistics/industry/tourism-and-transport/transport-census/2021)
- **Official Data Download:** [ABS Transport Data Summary Spreadsheet (.xlsx)](https://www.abs.gov.au/statistics/industry/tourism-and-transport/transport-census/2021/Transport%20data%20summary%20-%20first%20and%20second%20release.xlsx)
- **Census Variable Reference:** [ABS Census Dictionary — Method of Travel to Work (MTWP)](https://www.abs.gov.au/census/guide-census-data/census-dictionary/2021/variables-topic/transport/method-travel-work-mtwp)
- **City Planning Strategy:** [City of Melbourne — Transport Strategy 2030 (PDF)](https://www.melbourne.vic.gov.au/sites/default/files/2022-04/Transport-Strategy-2030.pdf)
- **Data File:** [Chart data](data/commute_trends_area.csv)

##### Dataset Background & Methodology
- **Scope & Geography:** Longitudinal time series of commuter travel into Central Melbourne (Place of Work / POWP = City of Melbourne / Melbourne CBD) across five national Census cycles: **2001, 2006, 2011, 2016, and 2021**.
- **Variables Queried:** Cross-tabulation of Census Year × Place of Work (POWP) × Method of Travel to Work (`MTWP`).
- **Mode Aggregation:**
  - **Private Car:** Motor vehicle drivers and passengers, trucks, and motorbikes.
  - **Public Transport:** Train, tram/light rail, bus, and ferry (including multi-modal public transport combinations).
  - **Walking:** Walked only.
  - **Cycling:** Bicycle (and multi-modal bicycle connections).
- **Units:** Thousands of daily inbound commuter trips (`daily_trips_k`).

##### Historical Trend Summary
- **2001–2016 (The Transit & Active Mode Shift):**
  - In 2001, **Private Car** was the dominant mode into central Melbourne (245k trips, 53.0%), with Public Transport carrying 180k (39.0%) and Cycling carrying 9k (1.9%).
  - By 2016, **Public Transport** surged to become the majority mode (310k trips, 51.1%), while Private Car declined to 215k trips (35.4%).
  - Cycling trips more than tripled from 9k (1.9%) in 2001 to 31k (5.1%) in 2016.
- **2021 Census (Pandemic Trends & Cycling Resilience):**
  - Total physical trips into the central city dropped from 607k to 437k due to widespread stay-at-home orders and remote work (38.6% of Melbourne workers worked from home on Census Day).
  - Despite overall volume drops, cycling retained 29k trips (6.6% of physical commuters), reflecting the resilience of active transport during the pandemic.

---

<a id="figure-9"></a>

#### Figure 9: Perceived cycling safety Likert bars (`data/safety_perception_likert.csv`)

- **Academic Institution:** [Monash University — Sustainable Mobility & Safety Research Group](https://research.monash.edu/en/persons/lauren-pearson), School of Public Health and Preventive Medicine (SPHPM).
- **Lead Researchers:** [Dr. Lauren Pearson](https://research.monash.edu/en/persons/lauren-pearson) & [Associate Professor Ben Beck](https://research.monash.edu/en/persons/ben-beck).
- **Primary Publications & Provenance:**
  1. Pearson, L., Dipnall, J., Gabbe, B., Braaf, S., White, S., Backhouse, M., & Beck, B. (2022). *The potential for bike riding across entire cities: Quantifying spatial variation in interest in bike riding.* **Journal of Transport & Health**, 24, 101290. [Monash Research Portal](https://research.monash.edu/en/publications/the-potential-for-bike-riding-across-entire-cities-quantifying-sp) · [DOI: 10.1016/j.jth.2021.101290](https://doi.org/10.1016/j.jth.2021.101290)
  2. Lim, T., Pearson, L., Thompson, J., Odgers, J. C., & Beck, B. (2023). *Establishing normative scores of affect, safety, and comfort for bicycling infrastructure and traffic conditions.* **Transportation Research Part F: Traffic Psychology and Behaviour**, 114, 337–353. [Monash Research Portal](https://research.monash.edu/en/publications/establishing-normative-scores-of-affect-safety-and-comfort-for-bi) · [DOI: 10.1016/j.trf.2025.06.006](https://doi.org/10.1016/j.trf.2025.06.006)
- **Survey Cohort:** Representative sample of $N = 3,993$ Victorian adults across Greater Melbourne and regional Victoria.
- **Data File:** [Chart data](data/safety_perception_likert.csv)

##### Survey Background & Methodology
- **Research Topic:** Subjective rider comfort, Level of Traffic Stress (LTS), and perceived safety across five diverse Australian infrastructure typologies.
- **Survey Instrument:** Five-point Likert scale measuring agreement with the statement: *"I feel safe riding on this type of road"* (*Strongly Disagree, Disagree, Neutral, Agree, Strongly Agree*).
- **Facilities Assessed (5 Typologies, N = 3,993):**
  1. **Separated Off-Road Path:** 90.2% positive agreement (52.4% Strongly Agree, 37.8% Agree, 5.9% Neutral, 2.7% Disagree, 1.2% Strongly Disagree).
  2. **Protected On-Road Cycleway:** 80.3% positive agreement (34.1% Strongly Agree, 46.2% Agree, 9.8% Neutral, 7.1% Disagree, 2.8% Strongly Disagree).
  3. **Painted On-Road Bike Lane:** 20.4% positive agreement (4.1% Strongly Agree, 16.3% Agree, 15.9% Neutral, 36.1% Disagree, 27.6% Strongly Disagree).
  4. **Mixed Traffic (Quiet Street):** 31.1% positive agreement (5.8% Strongly Agree, 25.3% Agree, 22.1% Neutral, 28.6% Disagree, 18.2% Strongly Disagree).
  5. **Arterial Road (No Bike Lane):** 1.8% positive agreement (0.3% Strongly Agree, 1.5% Agree, 3.2% Neutral, 21.2% Disagree, 73.8% Strongly Disagree).
- **Analytical Significance:** Demonstrates empirically that *"paint is not protection"*. While painted lanes require minimal capital outlay, 63.7% of surveyed adults feel unsafe using them, whereas physical protection achieves over 80% positive safety sentiment. This explains why 78% of Victorians remain in the "interested but concerned" near-market—willing to ride, but excluded by unprotected road designs.

---

<a id="figure-10"></a>

#### Figure 10: Bicycle trip purposes coxcomb (`data/trip_purpose_radial.csv`)

- **Primary Source Portal:** [Transport Victoria — VISTA Open Data Collection](https://opendata.transport.vic.gov.au/dataset/victorian-integrated-survey-of-travel-and-activity-vista)
- **State Repository:** [DataVic — Victorian Integrated Survey of Travel and Activity](https://discover.data.vic.gov.au/dataset/vista-victoria-integrated-survey-of-travel-and-activity)
- **Sample Cohort:** $N = 2,842$ bicycle trip stage records across Greater Melbourne
- **Data File:** [Chart data](data/trip_purpose_radial.csv)

##### Survey Background & Methodology
- **Survey Custodian:** Victorian Department of Transport and Planning (DTP) / Transport Victoria.
- **Methodology:** Filtered VISTA trip records across Greater Melbourne where travel mode is `Bicycle` (`linkmode` = Bicycle).
- **Variables Queried:** Trip Purpose (`linkpurpose` / `mainpurpose_desc`), survey sample counts (`sample_trips_n`), share of trips (`share_pct`), and average network trip distance (`avg_distance_km`).
- **Sample Breakdown (N = 2,842 surveyed bicycle trips):**
  - **Recreation & Exercise:** 34.0% of bicycle trips ($n = 966$ survey trips; avg distance **14.2 km**).
  - **Work Commuting:** 26.5% of bicycle trips ($n = 753$ survey trips; avg distance **8.6 km**).
  - **Utility & Shopping:** 18.2% of bicycle trips ($n = 517$ survey trips; avg distance **3.4 km**).
  - **Social & Dining:** 11.8% of bicycle trips ($n = 335$ survey trips; avg distance **4.8 km**).
  - **Education & School:** 9.5% of bicycle trips ($n = 271$ survey trips; avg distance **3.1 km**).
- **Idiom Design:** Equal-angle coxcomb (radial) chart where each purpose spans 72° (360° / 5), and the radius is scaled with a zero-based square-root transform (`type: "sqrt"`), ensuring wedge area is mathematically proportional to trip share.
- **Analytical Significance:** Disproves the common assumption that bicycle infrastructure only serves peak-hour office commutes. Work commutes account for only **26.5%** of trips; nearly three-quarters (73.5%) serve recreational, local shopping, social, and education journeys.

---

<a id="figure-11"></a>

#### Figure 11: Corridor gender split butterfly chart (`data/corridor_gender_split.csv`)

- **Primary Data Portal:** [City of Melbourne Open Data — Annual Bike Counts (Super Tuesday)](https://data.melbourne.vic.gov.au/explore/dataset/annual-bike-counts-super-tuesday/)
- **Survey Methodology:** [Bicycle Network Australia — Super Counts Methodology](https://bicyclenetwork.com.au/our-services/transport-surveys-and-data/super-counts/)
- **Data File:** [Chart data](data/corridor_gender_split.csv)

##### Idiom Design & Advanced Classification
- **Idiom Classification:** Advanced Idiom — Butterfly chart (bidirectional diverging horizontal bar chart).
- **Visual Encoding:** Female rider volumes extend to the left of the central zero baseline (`x = 0`) in teal (`#0d9488`), while male rider volumes extend to the right in slate (`#475569`). Both cohorts share a continuous horizontal quantitative scale, formatted with non-negative absolute tick labels (`abs(datum.value)`).
- **Design Rationale:** Unlike a grouped bar chart (which places bars side-by-side on a one-directional axis and is classified as a basic idiom), a butterfly chart mirrors the two cohorts across a common central spine. This produces a distinctive silhouette (the "butterfly wings") that immediately communicates the structural asymmetry between male and female participation across differing corridor environments.

##### Survey Background & Methodology
- **Data Provider:** City of Melbourne in partnership with Bicycle Network Australia (CC BY 4.0).
- **Collection Scope:** Manual morning-peak commuter count (7:00 am to 9:00 am) recording rider gender and directional flow.
- **Corridor Analysis (6 Key Arteries):**
  1. **Canning St (Carlton North):** 426 Female (38.0%), 694 Male (62.0%) — *Highest female participation (low-speed, traffic-calmed neighbourhood greenway).*
  2. **St Kilda Rd (Southbank):** 493 Female (34.0%), 957 Male (66.0%) — *Strong female participation on a major kerb-separated corridor.*
  3. **Upfield Path (Brunswick):** 317 Female (33.0%), 643 Male (67.0%) — *Off-road rail trail.*
  4. **Princes Bridge (Swanston St):** 400 Female (29.0%), 980 Male (71.0%) — *Central arterial gateway.*
  5. **Main Yarra Trail (Abbotsford):** 211 Female (27.0%), 569 Male (73.0%) — *Shared recreational corridor.*
  6. **Footscray Rd (West Melbourne):** 139 Female (17.0%), 681 Male (83.0%) — *Lowest female participation (hostile industrial freight corridor).*
- **Analytical Significance:** In international and Australian transport planning research, **female rider share is considered an "indicator species" of cycling infrastructure safety and quality**. Female participation is twice as high on calm, protected routes (38% on Canning St) compared to traffic-heavy, unseparated industrial roads (17% on Footscray Rd).


---

## Generative AI declaration

Gemini 3.8 Flash was used to assist with building the website's styles CSS code, formatting and structuring the layout, and compiling all references into neat formats.
