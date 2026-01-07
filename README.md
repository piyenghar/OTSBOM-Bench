# OTSBOM-Bench
OTSBOM-Bench is a curated benchmark of 38 expert-constructed SPDX SBOMs representing diverse operational technology (OT) device archetypes. The dataset includes gold labels for device type and component-level functional roles, enabling reproducible evaluation of semantic SBOM interpretation and architecture plausibility assessment.


### `sboms/`
- Contains **38 SPDX 2.3 SBOM files** in JSON format  
- Each SBOM represents **one OT device instance**
- SBOMs include firmware components, operating systems, protocol stacks, control logic, safety modules, and management services as appropriate for the device type
- SPDX relationships (e.g., `CONTAINS`) are used to encode architectural structure

### `gold/`
- Contains **38 gold-label JSON files**, each corresponding to exactly one SBOM
- Gold labels specify:
  - the **OT device type** (archetype)
  - the **functional role** of each in-scope software component

Gold labels are created independently of any automated tooling and represent expert judgment about typical OT device architectures.

---

## OT Device Archetypes

The dataset covers a broad range of **vendor-agnostic OT device archetypes**, including but not limited to:

- PLCs, PACs, Safety PLCs, and RTUs  
- DCS field control stations and engineering/maintenance stations  
- HMIs and operator workstations  
- Industrial gateways, routers, and protocol converters  
- OT security appliances (industrial firewalls, data diodes, network TAPs)  
- Drives, motion controllers, and safety devices  
- Sensors, actuators, and monitoring devices  
- Industrial PCs and OT server-class systems  

The complete list of device archetypes and their categorization is provided in:

- `devicelist_withoutLinks.json`

---

## Functional Role Taxonomy

Each software component in an SBOM is assigned a **functional role** describing its primary architectural responsibility. Examples include:

- `MainFirmware`
- `OS`
- `ProtocolStack`
- `LoggingMonitoring`
- `MeasurementAnalytics`
- `SecurityServices`
- `RoutingManagement`
- `SafetyLogic`
- `MotionControl`
- `Other`

Not all roles are valid for all device types.  
Device-specific constraints defining **which roles are permitted for each OT device archetype** are provided in:

- `allowed_roles_by_device_type.json`

These constraints are part of the dataset and enable explicit distinction between **in-scope** and **out-of-scope** role assignments.

---

## SBOM–Gold Label Correspondence

- Each SBOM file in `sboms/` has **exactly one corresponding gold-label file** in `gold/`
- Matching is performed by file name (e.g., `Dcs-Controller-1.json` ↔ `gold_Dcs-Controller-1_Task1.json`)
- Gold labels reference **SPDX package identifiers** to ensure unambiguous alignment between SBOM components and annotations

An example pair is provided for a **DCS field control station**, illustrating how operating systems, protocol stacks, control logic, redundancy management, and monitoring components are mapped to functional roles.

---

## Intended Use

OTSBOM-Bench is intended for:

- Benchmarking SBOM interpretation and consumption tools  
- Evaluating semantic reasoning over OT SBOMs  
- Studying architectural plausibility and completeness of OT SBOMs  
- Developing rule-based or model-based SBOM consumers  

The dataset is **not intended** for:

- Vulnerability or CVE benchmarking  
- Automated compliance certification  
- Vendor-specific SBOM assessment  

---

## Notes

- All SBOMs are **expert-constructed**, **vendor-agnostic**, and **architecturally plausible**
- The dataset emphasizes **semantic clarity** over exhaustive dependency enumeration
- The structure is fixed: **38 SBOMs and 38 corresponding gold labels**

---

## License

License information will be added to this repository.

---

## Citation

If you use this dataset in academic or industrial work, please cite the accompanying publication.  
A BibTeX entry will be added to this repository.
