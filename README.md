# CODE LIBRARY for SUB-NATIONAL TAILORING

**Version**: 11 September 2024  
**Authors**: Mohamed Kanu, Sammy Oppong, Jaline Gerardin

---

## 📂 Table of Contents

<details>
<summary>Overview</summary>

- [Motivation](#motivation)
- [Objectives](#objectives)
- [Target audience](#target-audience)
- [Scope](#scope)

</details>

<details>
<summary>A. DATA ASSEMBLY AND MANAGEMENT</summary>

- [A.1 Shapefiles](#a1-shapefiles)
  - Import shapefiles
  - Rename and match names
  - Link shapefiles to relevant scales
  - Visualizing shapefiles and making basic maps
- [A.2 Health Facilities](#a2-health-facilities)
  - Get MFL from the Malaria Program
  - Get DHIS2 Health Facility (HF) List from the Malaria Program
  - Reconciling the MFL and the DHIS2 HF list
  - HF active / inactive status
- [A.3 Routine case data from DHIS2](#a3-routine-case-data-from-dhis2)
  - Data extraction and import process
  - Sanity Checks (column names, dataset length)
  - Merging datasets, handling duplicates
  - Data cleaning (exploration, renaming variables, handling missing data)
  - Outlier detection and correction
- [A.4 DHS data](#a4-dhs-data)
- [A.5 Climate data](#a5-climate-data)
- [A.6 LMIS data](#a6-lmis-data)
- [A.7 Modeled data](#a7-modeled-data)
- [A.8 Population data](#a8-population-data)

</details>

<details>
<summary>B. EPIDEMIOLOGICAL STRATIFICATION</summary>

- [Reporting Rate per Variable](#b1)
- [Group and Merge Data](#b2)
- [Crude Incidence by Year](#b3)
- [Adjusted Incidence by Year](#b4)
- [Option to Select Incidence](#b5)
- [Risk Categorization](#b6)

</details>

<details>
<summary>C. STRATIFICATION OF OTHER DETERMINANTS</summary>

- [Access to Care](#c1)
- [Seasonality](#c2)
- [Insecticide Resistance](#c3)
- [Anti-Malaria Drug Resistance](#c4)

</details>

<details>
<summary>D. REVIEW OF PAST INTERVENTIONS</summary>

- [EPI Coverage and Dropout Rate](#d1)
- [IPTp and ANC Coverage](#d2)
- [PMC (Prevention of Malaria in Pregnancy)](#d3)
- [SMC (Seasonal Malaria Chemoprevention)](#d4)
- [Malaria Vaccine](#d5)
- [ITN Ownership, Access, Usage, and Type](#d6)
- [ITN Operational Coverage](#d7)
- [IRS (Indoor Residual Spraying)](#d8)
- [LSM (Larval Source Management)](#d9)
- [Assessing the Quality of Case Management](#d10)

</details>

<details>
<summary>E. Targeting of interventions</summary>
  
- [Link to section](#e)

</details>

<details>
<summary>F. Retrospective analysis</summary>

- [Link to section](#f)

</details>

<details>
<summary>G. Urban microstratification</summary>

- [Link to section](#g)

</details>

---

## NB

Draft document
