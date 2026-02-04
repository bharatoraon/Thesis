# Research framework refinement

## 1) Tightened problem statement
Urban transport planning in Indian metropolitan cities, including Chennai, has traditionally prioritized spatial expansion—adding routes, stations, and infrastructure. Yet passengers experience the system temporally: they incur waiting, transfer, and reliability penalties that are not captured by distance-based or proximity-based evaluations. In multimodal networks, poorly coordinated schedules and unreliable interchanges inflate total travel time and can unevenly burden peripheral and transit-dependent populations. These temporal inefficiencies are largely invisible in conventional accessibility metrics, risking overestimation of effective access and misdirected planning priorities.

This study addresses that gap by explicitly modeling time-based transfer performance and accessibility outcomes across Chennai’s multimodal public transport system (metro rail, bus, and suburban rail), quantifying transfer friction and its distributional consequences.

## 2) Research objectives
1. **Model temporal transfer performance** in a time-expanded multimodal network constructed from GTFS schedules and walking access links.
2. **Develop a Transfer Friction Index (TFI)** that integrates transfer waiting time, missed-connection probability, and access constraints at interchanges.
3. **Measure time-based accessibility** using realistic travel-time thresholds and compare results to conventional spatial (distance/proximity) measures.
4. **Assess temporal inequity** by aggregating accessibility and transfer-friction outcomes to wards and relating them to demographic context.
5. **Compare peak vs. off-peak conditions** to identify temporal variability in transfer friction and inequity.

## 3) Research questions
1. **How large is transfer friction across Chennai’s multimodal network, and where is it concentrated?**
2. **To what extent do time-based accessibility measures differ from spatial/proximity-based measures, and what does that imply for planning?**
3. **Which wards experience disproportionate temporal burdens (high transfer friction and low time-based accessibility), and how do these relate to socio-demographic patterns?**
4. **How do peak and off-peak operating conditions alter transfer friction and temporal inequity?**
5. **Which transfer penalties are primarily operational (schedule coordination) rather than infrastructural (network coverage)?**

## 4) Hypotheses / testable propositions
H1. **Areas with high physical connectivity can still exhibit low time-based accessibility** because transfer waiting and reliability penalties dominate effective travel times.

H2. **Transfer friction is spatially uneven**, with peripheral and transit-dependent wards experiencing significantly higher friction than centrally located wards.

H3. **Peak-hour coordination reduces average waiting time but increases missed-connection risk**, producing distinct spatial patterns of temporal inequity compared to off-peak conditions.

H4. **Time-based accessibility explains variation in ward-level accessibility better than spatial proximity alone**, indicating that distance-based measures systematically overestimate effective access.

H5. **A large share of observed transfer friction is operationally remediable**, implying that schedule coordination could yield substantial accessibility gains without major infrastructure expansion.

## 5) Positioning in existing literature (brief synthesis)
### Urban transport planning and accessibility
- Traditional planning emphasizes network expansion and spatial coverage; accessibility is often proxied by distance, service area buffers, or network topology.
- Contemporary accessibility research emphasizes travel-time thresholds, temporal reliability, and generalized cost, especially in multimodal systems.

### Transfer penalties and multimodal reliability
- Transfer penalties include expected waiting time, risk of missed connections, and perceived disutility; they can exceed in-vehicle time in shaping route choice.
- Empirical studies show that transfer reliability is a key determinant of passenger experience and system attractiveness, particularly where schedules are weakly coordinated.

### GTFS-based temporal analysis
- GTFS enables schedule-based modeling of public transport networks, supporting time-dependent routing, headway estimation, and transfer feasibility analysis.
- Time-expanded or time-dependent network models are increasingly used to evaluate operational performance and accessibility beyond static distance metrics.

### Equity and temporal inequity
- Equity research emphasizes unequal exposure to travel-time burdens across socio-demographic groups and geographies.
- Temporal inequity frameworks highlight that access quality varies not just spatially but also by time-of-day and reliability, affecting peripheral and lower-income populations disproportionately.

**Contribution of this study:** By integrating transfer friction with time-based accessibility at the ward scale, the study extends GTFS-based evaluation from network performance to distributional outcomes. It explicitly links operational coordination (transfers and schedules) to equity, highlighting where planning interventions can deliver time-based accessibility gains without new infrastructure.

---

## 6) Optional refinement: conceptual model (text description)
**Inputs:** GTFS schedules (bus, metro, suburban rail), walking access links, interchange locations, ward boundaries, demographic data.

**Process:** Build time-expanded multimodal network → calculate transfer waiting/missed-connection risk → compute TFI per interchange → route time-based OD accessibility → aggregate to wards → compare peak/off-peak → relate to demographics.

**Outputs:** Transfer friction hotspots, ward-level time-based accessibility, temporal inequity indicators, and policy-relevant recommendations.

---

## 7) Data already available in this repository (for immediate analysis)
### Metro rail (CMRL)
- **GTFS schedules:** `/workspace/Thesis/cmrl/CMRL gtfs/` (agency, calendar, routes, trips, stop_times, stops, transfers, shapes, fares).【F:cmrl/CMRL gtfs/agency.txt†L1-L2】
- **Station and line geometry:** entry/exit points, stations, corridors, and station boundary polygons in GeoJSON format (blue/green lines).【F:cmrl/Station_Entry_Exit_CMRL.geojson†L1-L2】

### Bus (MTC)
- **GTFS schedules:** `/workspace/Thesis/mtc/static_mtc_gtfs_data/` (agency, calendar, routes, trips, frequencies, stops; stop_times provided as `stop_times.zip`).【F:mtc/static_mtc_gtfs_data/agency.txt†L1-L2】
- **Network geometry:** bus stops, termini, and route polylines in GeoJSON format.【F:mtc/mtc_bus_stops_all.geojson†L1-L2】

### Suburban rail (Southern Railways)
- **Station and corridor geometry:** suburban stations, station codes, entry/exit points, and corridor geometry in GeoJSON format.【F:Southern Railways/suburban stations.geojson†L1-L2】
