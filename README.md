# S2X — SAS Code Intelligence & Modernization Framework

Client-Agnostic Framework for SAS Code Intelligence and Modernization  
A MicroZahn Product (Software Division of STAT X1, Inc.)

Initial development: 2025–2026

---

## 🔐 Intellectual Property Notice

S2X is a proprietary framework developed by MicroZahn, the software division of STAT X1, Inc., prior to and independent of any client engagements.

This repository provides a high-level overview and selected non-sensitive materials for demonstration purposes only.

The core engine, automation logic, and advanced capabilities are not included and remain confidential intellectual property.

---

## Overview

S2X is a code intelligence and transformation-readiness framework designed to analyze legacy SAS programs and generate structured, auditable Source-to-Target (S2T) mappings — without requiring access to underlying data.

S2X is designed to operate at scale across hundreds to thousands of SAS programs in enterprise environments.

The system enables organizations to:

- Understand complex SAS ETL environments  
- Extract business logic and transformation rules  
- Prepare for SAS-to-Python or platform modernization  
- Accelerate documentation and lineage efforts  

S2X is available as part of consulting engagements, assessment initiatives, and enterprise modernization programs.

What traditionally required weeks or months of manual analysis can now be completed in hours.

---

## Key Capabilities

### Code-Only Analysis
- No PHI, PII, or production data required  
- Operates on sanitized SAS programs  

### Source-to-Target Mapping (S2T)
- Variable-level lineage  
- Transformation logic extraction  
- Rule traceability back to source code  

### Macro-Aware Processing
- Handles complex macro-driven SAS logic  
- Preserves true execution behavior in analysis  

### Input / Output Dataset Detection
- Identifies datasets across DATA steps, PROC SQL, and ETL flows  
- Supports impact analysis and dependency mapping  

### Modernization Readiness
- Prepares SAS environments for Python, SQL, or cloud migration  
- Enables accurate scoping before redevelopment begins  

---

## ⚙️ S2X Workflow Overview

1. Input: SAS code (Data Step, PROC SQL, Macro-based pipelines)  
2. Phase 1: Parsing and normalization  
3. Phase 2: S2T (Source-to-Target) mapping generation  
4. Phase 3 (Planned): Automated Python and SQL ETL generation  

---

## Architecture Concept

S2X operates as a structured transformation pipeline:

```
Original SAS Code
        ↓
Normalized & Prepared Code
        ↓
Dataset Identification
        ↓
Macro-Aware Expansion
        ↓
Flattened Logical Representation
        ↓
Transformation Analysis Engine
        ↓
S2T Mapping Outputs (Excel / Structured Data)
```


Intermediate stages normalize and expand SAS logic into a structured, analyzable representation.

---

## 📌 Examples

Representative examples (SAS inputs and corresponding S2T outputs) will be added in a future update.

---

## Example Outputs

S2X produces structured outputs such as:

- Source-to-Target mapping tables  
- Variable-level transformation logic  
- Input-to-output dataset relationships  
- Rule-level traceability (IF / WHERE / CASE logic)  

These outputs are designed for:

- Data engineers  
- Business analysts  
- Modernization teams  
- Audit and compliance stakeholders  

---

## Design Principles

### Client-Agnostic
- No embedded schemas, data, or business rules  
- Portable across industries and environments  

### Data-Free Processing
- Operates entirely on code structure  
- Safe for restricted or regulated environments  

### Explainable Logic
- Every transformation traceable to source code  
- Supports audit and validation workflows  

### Modular Architecture
- Independent processing stages  
- Extensible to additional languages and platforms  

---

## 🚀 Future Capabilities

Planned extensions include automated generation of Python and SQL-based ETL pipelines from S2T mappings.

### → Code-2X (Future State)

- Multi-language code intelligence (SAS, SQL, ETL frameworks)  
- Cross-platform lineage extraction  
- Unified transformation mapping across data ecosystems  

---

## Use Cases

- SAS to Python migration planning  
- Legacy ETL reverse engineering  
- Rapid S2T documentation generation  
- Data lineage and governance initiatives  
- Pre-modernization system assessment  

---

## Repository Contents

- `docs/` — Process documentation and architecture  
- `examples/` — Sample inputs and outputs (sanitized) *(coming soon)*  
- `snippets/` — Illustrative code patterns (non-proprietary)  

---

## Status

This repository presents a high-level overview of the S2X framework, including workflow, architecture, and representative outputs.

The full engine, automation capabilities, and advanced implementation remain proprietary intellectual property of STAT X1, Inc.

---

## Contact Mike Krizan – S2X Founder

📧 **MikeKrizan@MicroZahn.com**  
📱 **(612) 594-2954**  
🔗 **[LinkedIn](https://www.linkedin.com/in/mike-krizan-microzahn)**  
📄 **Master’s Data Science Capstone – U.S. Health Insurance Cost Trends (2000–2023)**  
📄 **Capstone Report Available**  → **[View/Download Full 75-page PDF](https://github.com/MicroZahnAI/S2X/blob/main/capstone/04_Capstone_Full_Report/Krizan_Utica_MSDS_Health_Insurance_Costs_Capstone_2000-2023.pdf)**  
📍 Sioux Falls, SD

---

**Education**  
**M.S., Data Science** – Utica University (May 2025)  
**B.S., Agricultural Studies (Economics/Statistics)** – Iowa State University

---

## License
This repository is provided for informational and demonstration purposes.
All underlying methodologies, frameworks, and implementation logic are the intellectual property of STAT X1, Inc.
