# Data Dictionary: Sequence Abundance Matrix

Dataset type: sequence counts
Matching indicators: #NAME
Version: 0.1.0
Last updated: 2026-09-26

 
This document defines the schema, validation rules, naming conventions, and interpretation guidance for datasets containing bacterial taxonomic identifiers and sample-level sequence abundance measurements. 

---

## General Schema Summary

| Variable Pattern | Required | Format / Type | Validation Regex Pattern | Description | Allowed Values |
|------------------|----------|---------------|--------------------------|-------------|----------------|
| #NAME | Yes | Character | ^.+$ | Identifier bacterial taxa, enzyme, etc.  | Any non-empty string |
| [Sample_ID_Columns] | Yes | Measurement | ^.+$ | Sample-specific abundance count columns | Any non-negative integer |

---

## Identifier Rules

### #NAME

- `#NAME` is the primary identifier for bacterial taxa, enzyme, etc.
- Values must not be empty.
- Identifiers should be unique within a dataset.
- Identifiers should be treated as categorical labels.
- This field serves as the dataset primary key.

#### Examples

```text
Lactobacillus
Bacteroides
Escherichia-Shigella
Muribaculaceae
```

#### Validation

```regex
^.+$
```

---

## Sample Identifier Column Rules

### [Sample_ID_Columns]

The dataset contains one column per biological sample.

Column names represent sample identifiers


### Examples

```text
AJBcecum001
AJBcecum002
```

### Validation Pattern

#### Validation

```regex
^.+$
```

### Rules

- Sample identifier columns are required.
- Each sample column stores abundance measurements for each bacterial taxon.
- Sample columns function as foreign-key style identifiers linking taxa abundance values to biological samples. 

---

## Measurement Value Rules

All sample columns 