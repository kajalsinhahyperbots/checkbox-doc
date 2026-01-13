# Column Customization (Checkbox-Based Visibility)

## Overview

This document explains how dynamic column visibility is implemented in a React table using a checkbox-based selection mechanism.

The feature allows users to control which columns are displayed in the table at runtime. Columns can be enabled or disabled using a checklist, while mandatory columns remain permanently visible.

This pattern is commonly used in enterprise dashboards, reporting systems, and data-heavy user interfaces.

---

## Design Approach

The implementation follows these core principles:

1. **Single Source of Truth**  
   All column-related metadata (key, label, mandatory state) is defined in one configuration object.

2. **State-Driven Rendering**  
   The table UI is fully controlled by React state, ensuring predictable and consistent behavior.

3. **Scalable and Maintainable**  
   Adding or removing columns requires changes in only one place.

---

## High-Level Flow

1. Define all available columns in a configuration array.
2. Initialize state with mandatory columns.
3. Update state when a checkbox is toggled.
4. Render table headers and rows based on the current state.

---

## Column Configuration

All columns are defined in a single configuration object. Each column has:
- `key`: Unique identifier used for data access
- `label`: Display name shown in the UI
- `required`: Indicates whether the column is mandatory

```js
const ALL_COLUMNS = [
  // ===== DEFAULT COLUMNS (REQUIRED) =====
  {
    key: "customerLegalName",
    label: "Customer Legal Name",
    required: true
  },
  {
    key: "amountDue",
    label: "Amount Due",
    required: true
  },
  {
    key: "invoices",
    label: "Invoices",
    required: true
  },
  {
    key: "customerStatus",
    label: "Customer Status",
    required: true
  },
  {
    key: "assignedCollector",
    label: "Assigned Collector",
    required: true
  },

  // ===== OPTIONAL METADATA COLUMNS =====
  {
    key: "tags",
    label: "Tags",
    required: false
  },
  {
    key: "parentCompany",
    label: "Parent Company",
    required: false
  },
  {
    key: "countryRegion",
    label: "Country / Region",
    required: false
  },
  {
    key: "relationshipType",
    label: "Relationship Type",
    required: false
  },
  {
    key: "language",
    label: "Language",
    required: false
  },
  {
    key: "timezone",
    label: "Timezone",
    required: false
  }
];



