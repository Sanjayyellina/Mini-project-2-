# Mini-project-2-

Mapping NYC 311 Complaints Using Spatial Analysis

### 📌 Title and Objective

**Title**: *Where Do Public Complaints Cluster? A Spatial Analysis of NYC 311 Service Requests*

**Objective**:
The purpose of this project is to explore the geographic distribution of public complaints made to the NYC 311 system. By mapping complaints based on location and complaint type, I aimed to uncover spatial patterns, identify hotspots, and evaluate how different types of issues cluster across the five boroughs. This type of spatial analysis supports the public good by helping city officials, community leaders, and residents better understand where and what types of services are in high demand.

In particular, this project visualizes the five most common types of 311 complaints using two techniques: interactive marker clusters and density-based heatmaps. These maps reveal not only the volume but also the intensity and geographic concentration of service needs.

---

### 📊 Data Sources

* **Dataset**: NYC 311 Service Requests
* **Accessed via**: Socrata Open Data API (`erm2-nwe9`)
* **Timeframe**: Most recent 50,000 requests as of 2023
* **Fields Used**:

  * `complaint_type`, `descriptor`, `borough`, `status`
  * `latitude`, `longitude`, `created_date`

**Why this dataset?**
It offers both real-time feedback from residents and spatial coordinates for mapping. Since the complaints come directly from the public, the data provides a powerful and localized lens for measuring service quality, responsiveness, and neighborhood issues.

---

### 🛠️ Methods and Visual Tools

#### Step 1: Data Retrieval and Cleaning

* Pulled 50,000 rows using `sodapy`
* Filtered out entries with missing coordinates, boroughs, or complaint type
* Converted latitude and longitude to numeric values

#### Step 2: Identify Top Complaint Types

* Computed frequency of all `complaint_type` values
* Selected top 5 most reported complaints (e.g., Noise - Residential, Rodent, Illegal Parking, Blocked Driveway, HEAT/HOT WATER)

#### Step 3: Marker Cluster Map

* Used `folium` and `MarkerCluster` to plot each complaint
* Assigned a unique color to each complaint type
* Added an interactive legend that matched color to complaint type
* Included popup text showing type, status, and descriptor of each request

#### Step 4: Heatmap (Overall)

* Created a `folium.plugins.HeatMap` layer of all top 5 complaint types
* Used radius and blur settings to reflect complaint density
* Allowed viewers to visually detect general hotspots of civic activity

#### Step 5: Layered Heatmaps by Complaint Type

* Built a separate heatmap for each complaint type using `FeatureGroup`
* Displayed each complaint's heat layer individually, toggleable in map legend
* Included number of complaints in each layer name (e.g., "Noise - Residential (12,450 complaints)")

---

### 📈 Key Findings

* **Noise complaints** are heavily concentrated in Manhattan and parts of Brooklyn, especially in nightlife or densely populated areas
* **Rodent complaints** cluster most intensely in the Bronx and northern Manhattan, suggesting persistent sanitation or infrastructure issues
* **Illegal Parking and Blocked Driveway** issues dominate Queens and Brooklyn, likely due to residential street design and limited parking
* **HEAT/HOT WATER** complaints appear most frequently in the Bronx and parts of Brooklyn, especially in lower-income, high-density neighborhoods

The maps clearly show that different types of complaints cluster in different geographic zones, reflecting localized problems and patterns in civic life.

---

### 💬 Reflection

This project helped me understand how spatial analysis can enhance public data storytelling. While charts and tables are useful, maps bring the issues to life by showing *where* the problems occur. I also learned how to combine location data with categorical fields to make interactive maps that are both informative and user-friendly.

A key learning point was managing marker overload. Initially, I tried mapping all 50,000 complaints in one layer, which was unreadable. Breaking the data into layers by complaint type—and offering toggles with clear legends—made the map much more useful. I also appreciated the flexibility of `folium` for creating both marker-based and density-based maps.

If I continued this project, I would bring in demographic and housing data to explore whether complaint volume correlates with income, rent burden, or population density. I would also examine seasonal trends or changes in complaint types during holidays, weather shifts, or major city events.
