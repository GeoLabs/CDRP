# Key Steps in Developing the Shared Ontology:

**Concept Identification:**

* **Environmental Entities:** Identify and align concepts like weather, climate, water bodies, and ecological features from both OGC EDR and CCO.
* **Spatio-temporal:** Recognize and harmonize how both systems represent time (edr:time ↔ cco:TimeInterval) and space (edr:geometry ↔ cco:SpatialRegion).
* **Processes and Roles:** Align concepts related to data retrieval, environmental phenomena, and roles like data providers and consumers.

**Shared Concepts and Harmonization:**

* **Utilize CCO's Structure:** Leverage the existing structure of CCO to align with EDR concepts, ensuring compatibility.
* **Define Equivalence:** Establish clear equivalence relationships (e.g., owl:equivalentClass, owl:equivalentProperty) for concepts that are essentially the same in both systems.
* **Introduce Bridge Classes/Properties:** For concepts that are narrower or broader in one system compared to the other, introduce bridge classes or properties to maintain consistency.

**Ontology Creation Outline:**

* **Metadata Structure:** Map and align how environmental data formats, descriptions, and attributions are represented in both systems.
* **Spatio-temporal Dimensions:** Integrate and harmonize the representations of temporal and spatial dimensions.
* **Entities and Phenomena:** Align environmental entities (edr:DataEntity) with the entities and qualities defined within CCO.

**Mapping Framework Development:** Utilize RDF/OWL, a widely used language for representing knowledge in a machine-readable format, to create the formal mapping framework for the shared ontology.

### **Mapping of Core Concepts**

#### **Table 1: Core Concepts in OGC EDR and their CCO Counterparts**

| OGC EDR Concept | Concept Definition | CCO  | Remarks |
| ----- | ----- | ----- | ----- |
| `DataEntity` | Represents a data resource (e.g., dataset or observation). | `cco:PhysicalEntity` | Aligns environmental data with physical representations. |
| `Geometry` | Spatial description of the entity (e.g., bounding box, CRS). | `cco:SpatialRegion` | Use spatial definitions in CCO to describe extents. |
| `Time` | Temporal range of the dataset or event. | `cco:TimeInterval` | CCO’s temporal structure supports precise intervals. |
| `Parameter` | Describes the measured variables (e.g., temperature, humidity). | `cco:Quality` | Relates parameters to measurable qualities in CCO. |
| `CoverageType` | Type of coverage (e.g., point, trajectory, grid). | Custom mapping via bridge classes | Not directly in CCO, so bridge concepts are needed. |

#### **Table 2: Selected mappings between EDR and CCO concepts**

| OGC EDR Concept | CCO Concept | Mapping Example |
| ----- | ----- | ----- |
| Feature of Interest (FOI) | `cco:SpatialRegion` or `cco:MaterialEntity` | **Example**: A lake (`FOI`) \-\> `cco:SpatialRegion` represents its geographical extent. |
| Query (Spatial/Temporal) | `cco:Process` | **Example**: A temporal query to retrieve rainfall data \-\> `cco:Process` for data retrieval. |
| Variable (e.g., temperature) | `cco:Attribute` \+ `cco:UnitOfMeasure` | **Example**: Temperature \-\> `cco:Attribute` with `UnitOfMeasure` in Celsius. |
| Location (Coordinates) | `cco:Coordinate` | **Example**: A latitude-longitude point \-\> `cco:Coordinate`. |
| Temporal Interval | `cco:TimeInterval` | **Example**: 2023-01-01T00:00Z to 2023-01-02T00:00Z \-\> `cco:TimeInterval`. |

