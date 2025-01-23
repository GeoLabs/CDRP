# Use Cases for Mapping OGC EDR API to Common Core Ontology (CCO)

This document outlines three use cases that demonstrate how concepts from the OGC Environmental Data Retrieval (EDR) API can be mapped to the Common Core Ontology (CCO). These use cases involve semantic queries for flood-prone areas, temperature at a location, and average rainfall over a region.

## Use Case 1: Semantic Query for Flood-Prone Area

* **Objective:** To integrate flood-prone area data from the OGC Environment API with geospatial regions (e.g., hydrographic features) described in the CCO.
* **Query:** Identify and retrieve flood-prone areas and their spatial links to hydrographic features (e.g., rivers, floodplains).
* **Key Concepts:**
    * **OGC EDR API:**
        * `FloodingLocation`: Represents areas prone to flooding.
        * `Geometry`: Geospatial representation of flood-prone areas.
    * **CCO Ontology:**
        * `HydrographicFeature`: Represents water-related geographical entities like rivers, lakes, or basins.
        * `SpatialPart`: Links flood-prone areas to hydrographic features via spatial relationships.
* **Mappings:**
    * `OGC: FloodingLocation ↔ CCO: HydrographicFeature`
    * `OGC: Geometry ↔ CCO: SpatialPart`
* **SPARQL Query (Illustrative):** 
    * The document includes a SPARQL query for retrieving data related to precipitation and soil saturation, although this query does not directly map flood-prone areas to hydrographic features. 
    * The provided query looks for observations of precipitation within a date range and geospatial regions with soil saturation above 80%.
    * The query uses `cco:Process` for precipitation observations, `cco:GeospatialRegion` for spatial features, `cco:has_spatial_part` to link features with their coverage, and `cco:attribute` to specify the type of data. It also includes time filters and saturation value filters.
* **Mapped Concepts:**
    * `ogc:Observation → cco:Process`
    * `ogc:observedProperty → cco:attribute`
    * `ogc:hasTemporalExtent → cco:has_temporal_extent`
    * `ogc:startTime → cco:has_start_time`
    * `ogc:endTime → cco:has_end_time`
    * `ogc:Feature → cco:GeospatialRegion`
    * `ogc:hasCoverage → cco:has_spatial_part`
    * `ogc:observedProperty → cco:attribute`
    * `ogc:hasValue → cco:has_measurement_value`

## Use Case 2: Temperature at a Location

* **OGC EDR API Request:** Retrieve the temperature at location (35.6895°N, 139.6917°E) at 2023-01-01T12:00Z.
* **Mapped CCO Concepts:**
    * A `cco:Process` named :Request_001 has an input `cco:SpatialRegion` named :Location_001 and an output `cco:Attribute` named :Temperature_Reading_001, and occurs during the time interval :TimeInterval_2023-01-01_12:00Z.
    * The :Location_001 has coordinates of latitude "35.6895" and longitude "139.6917", linked through a `cco:Coordinate` named :Coordinate_Tokyo.
    * The :Temperature_Reading_001 has a value of "15.2" with a unit of measure in Celsius.

## Use Case 3: Average Rainfall Over a Region

* **OGC EDR API Request:** Retrieve the average rainfall in a bounding box region for the week of 2023-06-01 to 2023-06-07.
* **Mapped CCO Concepts:**
    * A `cco:Process` named :Request_002 has an input `cco:SpatialRegion` named :Region_BBox_001 and an output `cco:Attribute` named :Rainfall_Statistic_001, and occurs during the time interval :TimeInterval_2023-06.
    * The :Region_BBox_001 is defined by a bounding box :BBox_Coordinates_001, which is a `cco:SpatialRegion`, with a lower-left coordinate :Coordinate_LowerLeft (30.0, -100.0) and an upper-right coordinate :Coordinate_UpperRight (40.0, -90.0).
    * The :Rainfall_Statistic_001 has a value of "102.3" with a unit of measure in mm.

These use cases illustrate how various OGC EDR API concepts can be mapped to the CCO, enabling semantic interoperability and data integration across different systems. The use of `cco:Process`, `cco:SpatialRegion`, `cco:Attribute`, and related properties helps provide a structured way to represent environmental data and queries.