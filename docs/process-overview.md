# SAS-2X Process Overview

## High-Level S2T Generation Workflow

SAS-2X follows a structured, multi-step process to transform SAS code into
traceable, auditable Source-to-Target (S2T) mappings.

This workflow is designed to operate on sanitized code only, requiring no
access to underlying data.

---

## Step 01 — Code Preparation (Scrub Phase)

**Input:**
- Original SAS program (`*.sas`)

**Actions:**
- Remove comments and non-essential content
- Remove or redact PHI-sensitive elements
- Expand `%INCLUDE` references
- Preserve executable logic only

**Output:**
- Sanitized program:
  *_scrub00.sas

---

## Step 02 — Dataset Identification

**Program:**
- SAS-2X_Module01_ID_I-O_DSNs.sas

**Input:**
- `_scrub00.sas`

**Actions:**
- Parse SAS code to identify:
  - Input datasets
  - Output datasets
  - Library references (libname.dsname)

**Output:**
- Structured dataset inventory
- Used for traceability and controlled analysis

---

## Step 03 — Macro Expansion (Non-Destructive)

**Program:**
- SAS-2X_Module02_Scrub_Expand_Macro_from_SAS_Code.sas

**Inputs:**
- `_scrub00.sas`
- Dataset inventory from Step 02

**Actions:**
- Redirect datasets to WORK (safe execution)
- Execute SAS with `MPRINT` enabled
- Capture macro-expanded code
- Preserve execution logic without modifying source data

**Output:**
- Macro-expanded program:
  *_scrub00_mprint.sas

- Standardized as:
  *_scrub01.sas

---

## Step 04 — Logic Analysis (SPARq Engine)

**Program:**
- SAS-2X_Module03_SPARQ_Engine.sas

**Input:**
- `_scrub01.sas`
  (or `_scrub00.sas` if no macros exist)

**Actions:**
- Analyze:
  - DATA step transformations
  - PROC SQL logic
  - Joins and filters
  - Derived variables
- Capture:
  - Variable-level logic
  - Transformation rules
  - Lineage relationships

**Output:**
- Structured S2T documentation:
  S2T_<ProgramName>_<OutputDataset>.xlsx

---

## Key Characteristics

- **Code-Only Processing**
  - No production data required

- **PHI-Safe Workflow**
  - Operates on scrubbed programs only

- **Traceable Outputs**
  - All logic tied back to source code

- **Repeatable Framework**
  - Consistent across SAS environments

---

## Summary

SAS-2X transforms complex SAS programs into structured, explainable outputs
through a repeatable four-step process:

1. Scrub and prepare code  
2. Identify datasets  
3. Expand macros  
4. Analyze logic and generate S2T mappings  

This enables rapid understanding of legacy SAS environments and supports
modernization, migration, and governance initiatives.
