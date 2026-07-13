MENA Species Database

Structured ecological data for native and regionally adapted plant species of the UAE and Arabian Peninsula.

This repository provides curated, computable species data for use with [NatureOS Core](https://github.com/nature-os/core) and other ecological design, research, and conservation applications.

---

Contents

| File | Format | Description |
|------|--------|-------------|
| `data/species.json` | JSON | Full species dataset with ecological parameters |
| `data/species.csv` | CSV | Tabular format for spreadsheet and GIS import |
| `data/species.yaml` | YAML | Human-readable structured format |
| `docs/species-profiles/` | Markdown | Individual species profile sheets with ecological notes and references |

---

Data Structure

Each species record includes:

| Field | Type | Description |
|-------|------|-------------|
| `scientific_name` | string | Binomial name |
| `common_names` | array | Local and English common names |
| `family` | string | Botanical family |
| `growth_form` | enum | tree / shrub / grass / groundcover / climber / succulent / mangrove |
| `water_regime` | enum | very_low / low / moderate / high |
| `salinity_tolerance` | enum | none / low / moderate / high / halophyte |
| `thermal_tolerance` | enum | moderate / high / extreme |
| `ecosystems` | array | coastal_sabkha / mangrove_wetland / mountain_wadi / desert_scrub / urban_park |
| `mature_height_m` | float | Typical mature height in meters |
| `canopy_spread_m` | float | Typical canopy spread in meters |
| `root_depth_m` | float | Typical rooting depth in meters |
| `is_native` | boolean | Whether native to the Arabian Peninsula |
| `wildlife_value` | string | Description of ecological role |
| `carbon_potential` | enum | low / medium / high |
| `references` | array | Source publications or institutions |

---

Covered Ecosystems

- **Coastal sabkha and saline landscapes**
- **Mangrove and coastal wetlands**
- **Mountain wadi (Hajar range)**
- **Desert scrub and gravel plains**
- **Urban parks and streetscapes**

---

Reference Institutions

- Environment Agency – Abu Dhabi
- Dubai Municipality
- International Centre for Biosaline Agriculture (ICBA)
- Al Wathba Wetland Reserve
- Jebel Hafeet National Park

---

Usage

With NatureOS Core (Python)

```python
from natureos.data.mena_species import species_by_ecosystem
from natureos.species import EcosystemType

urban_trees = species_by_ecosystem(EcosystemType.URBAN_PARK)
for species in urban_trees:
    print(species.display_name)
Direct from JSON
python
import json

with open("data/species.json") as f:
    species = json.load(f)

native_drought_tolerant = [
    s for s in species
    if s["is_native"] and s["water_regime"] in ["very_low", "low"]
]
Contributing
See CONTRIBUTING.md for guidelines on submitting species data, corrections, and regional expansions.

License
Apache 2.0 — data is open for research, commercial use, and redistribution with attribution.

