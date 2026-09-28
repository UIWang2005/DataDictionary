# Data Dictionary: PCB Congener, PCB-derived analytes, and metabolites

- Dataset type: Measurement

- Matching indicators: sample_id

- Version: 0.1.0

Last updated: 2026-09-26


This document defines the schema, validation rules, naming conventions, and interpretation guidance for datasets containing polychlorinated biphenyl (PCB) measurements and PCB-derived analytes.

## General Schema Summary

| Variable Pattern | Required | Format / Type | Validation Regex Pattern | Description | Allowed Values |
|---|---|---|---|---|---|
| sample_id | Yes | String | ^.+$ | Unique sample identifier representing a sample, batch, experiment, participant, location, analytical unit, or other study-specific identifier. | Any non-empty string |
| PCB\d+([.+]\d+)* | No | Measurement | ^PCB\d+([.+]\d+)*$ | Parent PCB congeners and composite PCB congener groups. | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |
| (\d+'?(,\d+'?)*)-(di)?OH-PCB\d+ | No | Measurement | ^(\d+'?(,\d+'?)*)-(di)?OH-PCB\d+$ | Hydroxylated PCB metabolites (OH-PCBs). | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |
| (\d+'?(,\d+'?)*)-(di)?MeO-PCB\d+ | No | Measurement | ^(\d+'?(,\d+'?)*)-(di)?MeO-PCB\d+$ | Methoxylated PCB metabolites (MeO-PCBs). | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |
| (\d+'?(,\d+'?)*)-PCB\d+-Sulfate | No | Measurement | ^(\d+'?(,\d+'?)*)-PCB\d+-Sulfate$ | PCB-Sulfate metabolites. | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |
| Cl\d+_OH-PCB(_\d+)? | No | Measurement | ^Cl\d+_OH-PCB(_\d+)?$ | Chlorinated hydroxylated PCB metabolite classes | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |
| Cl\d+_diOH-PCB(_\d+)? | No | Measurement | ^Cl\d+_diOH-PCB(_\d+)?$ | Chlorinated dihydroxylated PCB metabolite classes | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |
| Cl\d+_PCB-Sulfate(_\d+)? | No | Measurement | ^Cl\d+_PCB-Sulfate(_\d+)?$ | PCB sulfate metabolite classes | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |
| Cl\d+_PCB-Sulfonate(_\d+)? | No | Measurement | ^Cl\d+_PCB-Sulfonate(_\d+)?$ | PCB sulfonate metabolite classes | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |
| Cl\d+_OH-PCB-Sulfate(_\d+)? | No | Measurement | ^Cl\d+_OH-PCB-Sulfate(_\d+)?$ | Hydroxylated PCB sulfate metabolite classes | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |
| Cl\d+_OH-PCB-Sulfonate(_\d+)? | No | Measurement | ^Cl\d+_OH-PCB-Sulfonate(_\d+)?$ | Hydroxylated PCB sulfonate metabolite classes | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |
| Cl\d+_MeO-OH-PCB(_\d+)? | No | Measurement | ^Cl\d+_MeO-OH-PCB(_\d+)?$ | Methoxy-hydroxylated PCB metabolite classes | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |
| Cl\d+_MeO-PCB-Sulfate(_\d+)? | No | Measurement | ^Cl\d+_MeO-PCB-Sulfate(_\d+)?$ | Methoxylated PCB sulfate metabolite classes | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |
| F-PCB-Sulfate | No | Measurement | ^F-PCB-Sulfate$ | Fluorinated PCB sulfate metabolite class | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |
| F-OH-PCB | No | Measurement | ^F-OH-PCB$ | Fluorinated hydroxylated PCB metabolite class | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |
| \d+'?-F-OH-PCB\d+ | No | Measurement | ^\d+'?-F-OH-PCB\d+$ | Fluorinated hydroxylated PCB congeners | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |


## Identifier Rules

### sample_id
- sample_id is the primary sample identifier.
- Values must not be empty.
- Identifiers should be unique within a dataset when used as record keys.
- Identifiers should be treated as categorical labels.

### Examples
```text
B01
Sample_001
Subject_012
QC_Blank_03
AirPUF_2026_001
```

---

## Parent PCB Congeners

### Examples
```text
PCB1
PCB10
PCB52
PCB126
PCB203
```
### Rules
- Space between PCB and congener number is not allowed.

---

## Composite PCB Congener Groups
### Examples 
```text
PCB12.13
PCB44.47.65
PCB90+101+113
PCB129+138+163
PCB147+149
PCB153+168
PCB198+199
```

### Rules

- `.` and `+` are PCB congener separators.
- `.` is not a decimal indicator.
- `+` is not an arithmetic operator.
- Composite identifiers represent grouped analytical measurements.
- Variable names must be preserved exactly as reported.

---

## Hydroxylated PCB Metabolites (OH-PCBs)
### Examples
```text
4'-OH-PCB3
3'-OH-PCB138
5-OH-PCB183
3',4-diOH-PCB90
```

### Rules

- Prefix numbers indicate hydroxyl substitution positions.
- Apostrophes (`'`) are significant.
- `diOH` indicates multiple hydroxyl substitutions.
- Variable names must be preserved exactly as reported.

---

## Methoxylated PCB Metabolites (MeO-PCBs)
### Examples
```text
4-MeO-PCB1
4'-MeO-PCB198
5-MeO-PCB183
4,5-diMeO-PCB91
```

### Rules

- Prefix numbers indicate methoxy substitution positions.
- Apostrophes are significant.
- `diMeO` indicates multiple methoxy substitutions.
- Variable names must be preserved exactly as reported.

---

## PCB Sulfate Metabolites
### Examples
```text
4-PCB1-Sulfate
4'-PCB12-Sulfate
4-PCB107-Sulfate
```

### Rules

- There is no space preceding the word `sulfate`.
- Prefix numbers indicate sulfate substitution positions.
- Apostrophes are significant.
- Variable names must be preserved exactly as reported.

---

## Additional PCB Metabolite Group Variables

### Rules
- Cl# indicates degree of chlorination.
- F indicates fluorinated PCB metabolite analogs.
- Suffixes such as _1, _2, _3 denote analytically resolved features or isomers.
- Hyphens and underscores are significant.
- Sulfate and sulfonate metabolites are distinct analyte classes.
- Variable names must be preserved exactly as reported.

### Representative Examples

```text
F-PCB-Sulfate
F-OH-PCB
3-F-OH-PCB3
Cl3_PCB-Sulfate_1
Cl1_PCB-Sulfonate_1
Cl2_diOH-PCB
Cl1_OH-PCB-Sulfate_1
Cl1_OH-PCB-Sulfonate
Cl5_MeO-OH-PCB_1
Cl5_MeO-PCB-Sulfate_2
```
---

## Measurement Value Rule

All PCB-related measurement variables may contain either a numeric concentration or an approved reporting code.

### Numeric Measurements
Allowed range: > 0.0

### Reporting Codes
<empty cell> = Not available
0 = Non-detect
ND = Non-detect
NA = Not available
N/A = Not applicable

## Validation Rules Summary

| Rule | Constraint |
|---|---|
| sample_id | Required and must be a non-empty string |
| Parent PCB identifiers | Must match PCB naming conventions |
| OH-PCB identifiers | Must match ^(\d+'?(,\d+'?)*)-(di)?OH-PCB\d+$ |
| MeO-PCB identifiers | Must match ^(\d+'?(,\d+'?)*)-(di)?MeO-PCB\d+$ |
| PCB sulfate identifiers | Must match ^(\d+'?(,\d+'?)*)-PCB\d+-Sulfate$ |
| Chlorinated metabolite classes | Must match defined Cl-class regex patterns |
| Fluorinated metabolite classes | Must match defined F-class regex patterns |
| Measurement values | Numeric value > 0.0, ND, NA, N/A, or blank (missing) |
| Variable names | Must preserve original identifiers exactly |

## Version Information

| Attribute | Value |
|---|---|
| Dataset Family | PCB Congeners and PCB-Derived Metabolites |
| Primary Identifier | sample_id |
| Allowed Reporting Codes | ND, NA, N/A, blank (missing) |
| Additional Metabolite Classes | Supported |
