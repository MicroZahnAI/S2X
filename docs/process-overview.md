# S2X Process Overview
*This document provides a high-level process overview.  
Implementation details and internal automation components are proprietary to MicroZahn (STAT X1, Inc.).*  

S2X is designed to operate at scale across large SAS environments, including hundreds to thousands of programs.

## High-Level S2T Generation Workflow

S2X follows a structured, multi-stage process to transform SAS code into traceable, auditable Source-to-Target (S2T) mappings.

This workflow operates on sanitized code only and does not require access to underlying data.

---

## Step 01 — Code Preparation

**Input:**
- Original SAS program (`*.sas`)

**Actions:**
- Remove comments and non-essential content  
- Redact or exclude sensitive elements  
- Resolve external code references  
- Preserve executable logic only  

**Output:**
- Normalized, analysis-ready SAS code  

---

## Step 02 — Dataset Identification

**Input:**
- Prepared SAS code  

**Actions:**
- Identify:
  - Input datasets  
  - Output datasets  
  - Library and reference structures  

**Output:**
- Structured dataset inventory  
- Foundation for lineage and dependency mapping  

---

## Step 03 — Macro-Aware Expansion

**Input:**
- Prepared SAS code  
- Dataset inventory  

**Actions:**
- Expand macro-driven logic into analyzable form  
- Preserve execution behavior  
- Normalize dynamic and macro-driven code structures 

**Output:**
- Flattened, macro-resolved SAS logic  

---

## Step 04 — Logic Analysis & S2T Generation

**Input:**
- Flattened SAS logic  

**Actions:**
- Analyze:
  - DATA step transformations  
  - PROC SQL logic  
  - Joins, filters, and conditional rules  
  - Derived variable construction  

- Extract:
  - Variable-level transformation logic  
  - Rule definitions  
  - Source-to-target lineage relationships  

**Output:**
- Structured, auditable S2T documentation  
- Transformation-ready mapping outputs  

---

## Key Characteristics

### Code-Only Processing
- No production data required  

### PHI-Safe Workflow
- Operates exclusively on sanitized code  

### Traceable Outputs
- All transformations are linked back to source logic  

### Repeatable Framework
- Consistent across diverse SAS environments  

---

## Summary

S2X transforms complex SAS programs into structured, explainable outputs through a repeatable four-stage process:

1. Prepare and normalize code  
2. Identify datasets and dependencies  
3. Expand macro-driven logic  
4. Analyze transformations and generate S2T mappings  

This process enables rapid understanding of legacy SAS environments and supports modernization, migration, and governance initiatives.
