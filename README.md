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
| Safety | Grouped bars | Compare gender counts at selected corridors |

There are 11 charts and three distinct map idioms. Maps, waffle, bump, heatmap, coxcomb and treemap provide eight advanced idioms, complemented by diverging stacked bars, grouped bars and stacked area charts.

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
- **Spatial Infrastructure Dataset:** [Transport Victoria — Bicycle Infrastructure Network (BIN)](https://opendata.transport.vic.gov.au/dataset/bicycle-infrastructure-network)
- **State Repository:** [DataVic — Bicycle Infrastructure Network](https://discover.data.vic.gov.au/dataset/bicycle-infrastructure-network)
- **Ridership Volumes:** [City of Melbourne — Annual Bike Counts (Super Tuesday)](https://data.melbourne.vic.gov.au/explore/dataset/annual-bike-counts-super-tuesday/) & [Bicycle Counter Network](https://data.melbourne.vic.gov.au/)
- **Data File:** [Chart data](data/cycling_routes.geojson)

##### How the Dataset Was Created
1. **Corridor Selection (12 Major Melbourne Arteries):**
   Selected 12 key commuter corridors radiating through Greater Melbourne to capture the diversity of infrastructure types:
   - **Off-Road Shared Trails (6):** Capital City Trail, Main Yarra Trail, Upfield Bike Path, Bay Trail (St Kilda to Brighton), Gardiners Creek Trail, Maribyrnong River Trail.
   - **Protected On-Road Corridors (4):** St Kilda Road Cycleway, Canning Street Corridor, Albert Street Cycleway, Footscray Road Veloway.
   - **Painted On-Road Lanes (2):** Sydney Road Bike Lanes, Chapel Street Mixed Corridor.

2. **Spatial Geometry Compilation:**
   - Centerline coordinates were traced following the official alignments defined in the Victorian Government Strategic Cycling Corridors (SCC) spatial network and OpenStreetMap / Victorian road centerline databases.
   - Coordinate format: GeoJSON `LineString` using WGS84 (`[longitude, latitude]`) geographic coordinates.

3. **Protection Level Classification (`quality_tier`):**
   Corridors were classified into three standardized tiers according to Victorian DTP Active Transport Infrastructure Design Guidelines:
   - **`Separated Off-Road`**: Fully grade-separated paths in parklands, river corridors, or rail reserves, isolated from motorized vehicle traffic.
   - **`Protected On-Road`**: Physically separated lanes positioned within road reserves, segregated from motor traffic by concrete kerbs, parked cars, or continuous physical barriers (e.g., St Kilda Rd protected bike lanes).
   - **`Painted On-Road Lane`**: On-street bicycle lanes defined solely by white paint markings on road asphalt, exposing cyclists to motor traffic and car-door hazards (e.g., Sydney Rd).

4. **Ridership Volume Compilation (`daily_volume`):**
   - Benchmark average daily cyclist volumes were compiled from City of Melbourne permanent automated counter stations and the Bicycle Network Australia Annual Bike Count database.
   - Values range from **1,200** daily riders on constrained corridors (Chapel St) to **6,200** daily riders on flagship arteries (St Kilda Rd).

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
- Aggregated average hourly cyclist counts across all 24 hours of the day across 7 days of the week.
- Demonstrates clear bimodal weekday commuter spikes (7:00–9:00 am and 4:30–6:30 pm) versus unimodal midday weekend recreation peaks.

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
- **2021 (COVID-19 Lockdown 6 Anomaly):**
  - Total physical trips into the central city dropped from 607k to 437k due to widespread stay-at-home orders and remote work (38.6% of Melbourne workers worked from home on Census Day).
  - Despite overall volume drops, cycling retained 29k trips (6.6% of physical commuters), reflecting the resilience of active transport during the pandemic.

---

<a id="figure-9"></a>

#### Figure 9: Perceived cycling safety Likert bars (`data/safety_perception_likert.csv`)

- **Primary Organisation:** [Bicycle Network Australia](https://bicyclenetwork.com.au/)
- **Research Institute:** [Monash University Accident Research Centre (MUARC)](https://www.monash.edu/muarc) *(straight from our very own uni at Clayton — proving scientifically what every Monash student already knew: paint is not protection!)*
- **Monash Academic Study (Passing Distances & Infrastructure):** [Monash University — "More than a stripe of paint needed to keep cyclists safe"](https://www.monash.edu/news/articles/more-than-a-stripe-of-paint-needed-to-keep-cyclists-safe)
- **Monash Public Health Research:** [Monash Medicine — "3 in 4 people want to ride a bike, but are put off by lack of safe lanes"](https://www.monash.edu/medicine/news/latest/2022-articles/3-in-4-people-want-to-ride-a-bike-but-are-put-off-by-lack-of-safe-lanes)
- **Data File:** [Chart data](data/safety_perception_likert.csv)

##### Survey Background & Methodology
- **Research Topic:** Rider comfort, Level of Traffic Stress (LTS), and perceived safety across diverse bicycle infrastructure typologies.
- **Survey Instrument:** Five-point Likert scale measuring agreement with the prompt: *"I feel safe riding on this type of road"* (*Strongly Disagree, Disagree, Neutral, Agree, Strongly Agree*).
- **Facilities Assessed (5 Real-World Typologies):**
  1. **Separated Off-Road Path:** 90% positive agreement (52% Strongly Agree, 38% Agree, 6% Neutral, 4% Disagree).
  2. **Protected On-Road Cycleway:** 80% positive agreement (34% Strongly Agree, 46% Agree, 10% Neutral, 10% Disagree).
  3. **Painted On-Road Bike Lane:** Only 20% positive agreement (4% Strongly Agree, 16% Agree, 16% Neutral, 64% Disagree).
  4. **Mixed Traffic (Quiet Street):** 31% positive agreement (6% Strongly Agree, 25% Agree, 22% Neutral, 47% Disagree).
  5. **Arterial Road (No Bike Lane):** Just 2% positive agreement; **95% negative agreement** (74% Strongly Disagree, 21% Disagree).
- **Analytical Significance:** Demonstrates the principle that *"paint is not protection"*. While painted lanes require low capital outlay, nearly two-thirds (64%) of riders feel unsafe using them, explaining why physical segregation is necessary to encourage hesitant cyclists.

---

<a id="figure-10"></a>

#### Figure 10: Bicycle trip purposes coxcomb (`data/trip_purpose_radial.csv`)

- **Primary Source Portal:** [Transport Victoria — VISTA Open Data Collection](https://opendata.transport.vic.gov.au/dataset/victorian-integrated-survey-of-travel-and-activity-vista)
- **State Repository:** [DataVic — Victorian Integrated Survey of Travel and Activity](https://discover.data.vic.gov.au/dataset/vista-victoria-integrated-survey-of-travel-and-activity)
- **Data File:** [Chart data](data/trip_purpose_radial.csv)

##### Survey Background & Methodology
- **Survey Custodian:** Victorian Department of Transport and Planning (DTP) / Transport Victoria.
- **Methodology:** Filtered VISTA trip records across Greater Melbourne where travel mode is `Bicycle` (`linkmode` = Bicycle).
- **Variables Queried:** Trip Purpose (`linkpurpose` / `mainpurpose_desc`), annualised grossed trip counts, and average trip distance (`VISTADIST` in km).
- **Purpose Breakdown:**
  - **Recreation & Exercise:** 34.0% of bicycle trips (47.6 million annual trips; avg distance **14.2 km**).
  - **Work Commuting:** 26.5% of bicycle trips (37.1 million annual trips; avg distance **8.6 km**).
  - **Utility & Shopping:** 18.2% of bicycle trips (25.5 million annual trips; avg distance **3.4 km**).
  - **Social & Dining:** 11.8% of bicycle trips (16.5 million annual trips; avg distance **4.8 km**).
  - **Education & School:** 9.5% of bicycle trips (13.3 million annual trips; avg distance **3.1 km**).
- **Idiom Design:** Equal-angle coxcomb (radial) chart where each purpose spans 72° (360° / 5), and the radius is scaled with a zero-based square-root transform (`type: "sqrt"`), ensuring wedge area is mathematically proportional to trip share.
- **Analytical Significance:** Disproves the common assumption that bicycle infrastructure only serves peak-hour office commutes. Work commutes account for only **26.5%** of trips; nearly three-quarters (73.5%) serve recreational, local shopping, social, and education journeys.

---

<a id="figure-11"></a>

#### Figure 11: Corridor gender counts grouped bars (`data/corridor_gender_split.csv`)

- **Primary Data Portal:** [City of Melbourne Open Data — Annual Bike Counts (Super Tuesday)](https://data.melbourne.vic.gov.au/explore/dataset/annual-bike-counts-super-tuesday/)
- **Survey Methodology:** [Bicycle Network Australia — Super Counts Methodology](https://bicyclenetwork.com.au/our-services/transport-surveys-and-data/super-counts/)
- **Data File:** [Chart data](data/corridor_gender_split.csv)

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

Gemini 3.8 Flash was used to assist with building the website's styles CSS code alongside formatting the references and compiling them into neat formats, and was also used to scrape data from [Bicycle Network](https://bicyclenetwork.com.au/) which had the dataset locked behind a subscription.
