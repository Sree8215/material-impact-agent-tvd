# Material Change Data Contract

This document defines the mandatory structure for a material change
event evaluated by the Material Impact Agent.

The system must reject any input that does not conform to this contract.

---

## Required Fields

### element_id
- Type: string
- Description: Unique identifier of the building element (from BIM/IFC)
- Example: `WALL_L2_034`

### old_material_code
- Type: string
- Description: Code or identifier of the existing material
- Example: `CONC_C30_STD`

### new_material_code
- Type: string
- Description: Code or identifier of the proposed material
- Example: `CONC_C30_LOW_CARBON`

### quantity
- Type: number
- Description: Quantity of material affected by the change
- Unit must be provided separately
- Example: `45.6`

### unit
- Type: string
- Allowed values: `m3`, `m2`, `kg`, `t`, `count`
- Example: `m3`

---

## Optional Fields

### location
- Type: string
- Description: Spatial or system grouping (e.g., Level, Zone)
- Example: `Level 2`

### discipline
- Type: string
- Description: Originating discipline of the change
- Example: `Structural`

---

## Validation Rules

- quantity must be > 0
- unit must be compatible with material type
- old_material_code and new_material_code must exist in:
  - cost database
  - LFC dataset
  - carbon dataset

If any validation fails, the system must halt execution and report the error.
