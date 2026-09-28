# Data Dictionary: KEGG Enrichment Analysis Results

This document defines the schema, validation rules, and semantic mappings for KEGG pathway enrichment analysis results generated from GSEA or related enrichment workflows.

## General Schema Summary

| Variable Name | Display Name | Description | Data Type | Unit | Allowed Values | Example Value | Required | Primary Key |
|---------------|--------------|-------------|------------|------|----------------|--------------|----------|-------------|
| ID | KEGG Pathway Identifier | Unique KEGG pathway identifier. | character | NA | Valid KEGG pathway identifiers | ko00260 | Yes | Yes |
| Description | KEGG Pathway Name | Human-readable name of the KEGG pathway. | character | NA | KEGG pathway names | Glycine, serine and threonine metabolism | Yes | No |
| setSize | Pathway Gene Count | Number of genes or KEGG orthologs assigned to the pathway included in enrichment analysis. | integer | count | Positive integers | 44 | Yes | No |
| enrichmentScore | Enrichment Score | Raw enrichment score (ES). Positive values indicate enrichment and negative values indicate depletion. | numeric | NA | Real numbers | 0.52 | Yes | No |
| NES | Normalized Enrichment Score | Enrichment score normalized for pathway size to enable comparisons across pathways. | numeric | NA | Real numbers | 1.35 | Yes | No |
| pvalue | Nominal P-Value | Nominal p-value associated with the enrichment score. | numeric | NA | 0-1 | 0.023 | Yes | No |
| p.adjust | Adjusted P-Value | Multiple-testing corrected p-value. | numeric | NA | 0-1 | 0.042 | Yes | No |
| qvalue | False Discovery Rate | Estimated false discovery rate associated with pathway enrichment. | numeric | NA | 0-1 | 0.061 | Yes | No |
| rank | Peak Enrichment Rank | Position within the ranked feature list at which the enrichment score reaches maximum deviation from zero. | integer | rank | Positive integers | 324 | Yes | No |
| leading_edge | Leading Edge Summary | Summary statistics describing the subset of genes contributing most strongly to pathway enrichment. | character | NA | GSEA formatted text | tags=35%, list=20%, signal=28% | Yes | No |
| core_enrichment | Core Enrichment Orthologs | KEGG ortholog identifiers comprising the leading-edge subset responsible for enrichment. | character | NA | KEGG Orthology identifiers | K00844/K01810 | Yes | No |

---

## Variable Definitions

### ID
- Primary identifier for each KEGG pathway.
- Must contain a valid KEGG pathway ID.
- Values must be unique within a dataset.

#### Example
```
ko00260
```

---

### Description
- Human-readable KEGG pathway name.
- Corresponds to the pathway represented by `pathway_id`.

#### Example
```
Glycine, serine and threonine metabolism
```

---

### setSize
- Number of genes or KEGG orthologs assigned to the pathway.
- Must be a positive integer.

#### Example
```
44
```

---

### enrichmentScore
- Raw enrichment score (ES).
- Positive values indicate enrichment.
- Negative values indicate depletion.
- Real numeric values allowed.

#### Example
```
0.52
```

---

### NES
- Normalized Enrichment Score.
- Allows comparison among pathways of different sizes.
- Real numeric values allowed.

#### Example
```
1.35
```

---

### pvalue
- Nominal p-value associated with enrichment.
- Allowed range: 0 to 1.

#### Example
```
0.023
```

---

### p.adjust
- Multiple-testing corrected p-value.
- Allowed range: 0 to 1.

#### Example
```
0.042
```

---

### qvalue
- Estimated false discovery rate (FDR).
- Allowed range: 0 to 1.

#### Example
```
0.061
```

---

### rank
- Position in the ranked feature list where enrichment reaches maximum deviation from zero.
- Must be a positive integer.

#### Example
```
324
```

---

### leading_edge
- Summary statistics describing the leading-edge subset.
- Stored as GSEA-formatted text.

#### Example
```
tags=35%, list=20%, signal=28%
```

---

### core_enrichment
- KEGG ortholog identifiers contributing to pathway enrichment.
- Typically represented as slash-delimited KEGG Orthology IDs.

#### Example
```
K00844/K01810
```

---

## Ontology and FAIR Mapping

| Variable | FAIR Mapping | Ontology ID | Ontology Label |
|----------|--------------|-------------|----------------|
| ID | PathwayIdentifier | KEGG:PATHWAY | KEGG Pathway |
| Description | PathwayLabel | SIO:000185 | Label |
| setSize | GeneSetCardinality | SIO:000794 | Count |
| enrichmentScore | GSEAEnrichmentScore | EDAM:data_2526 | Statistical score |
| NES | GSEANormalizedEnrichmentScore | EDAM:data_2526 | Statistical score |
| pvalue | NominalPValue | STATO:0000184 | P-value |
| p.adjust | MultipleTestingAdjustedPValue | STATO:0000411 | Adjusted p-value |
| qvalue | FalseDiscoveryRate | STATO:0000304 | False discovery rate |
| rank | RankPosition | STATO:0000293 | Rank |
| leading_edge | LeadingEdgeSummary | MARBLES:GSEA_LEADING_EDGE | Leading Edge Summary |
| core_enrichment | LeadingEdgeGeneSet | MARBLES:CORE_ENRICHMENT_SET | Core Enrichment Ortholog Set |

---

## Validation Rules Summary

| Rule | Constraint |
|--------|------------|
| ID | Required, unique, valid KEGG pathway identifier |
| Description | Required, non-empty pathway name |
| setSize | Required, integer > 0 |
| enrichmentScore | Required numeric value |
| NES | Required numeric value |
| pvalue | Required numeric value between 0 and 1 |
| p.adjust | Required numeric value between 0 and 1 |
| qvalue | Required numeric value between 0 and 1 |
| rank | Required positive integer |
| leading_edge | Required GSEA formatted text |
| core_enrichment | Required KEGG ortholog identifier list |

---

## Missing Value Definitions

| Variable | Missing Value Definition |
|-----------|--------------------------|
| ID | Not allowed |
| Description | Not allowed |
| setSize | NA |
| enrichmentScore | NA |
| NES | NA |
| pvalue | NA |
| p.adjust | NA |
| qvalue | NA |
| rank | NA |
| leading_edge | NA |
| core_enrichment | NA |

---

## Version Information

| Attribute | Value |
|------------|--------|
| Dataset Family | KEGG Enrichment Analysis |
| Primary Identifier | ID |
| Statistical Framework | GSEA-compatible enrichment |
| Controlled Vocabulary | KEGG Pathway Ontology, KEGG Orthology, EDAM, STATO |
| FAIR Mapping | Included |


## Reference

clusterProfiler package