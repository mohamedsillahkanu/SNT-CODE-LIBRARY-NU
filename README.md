# CODE LIBRARY for SUB-NATIONAL TAILORING

**Version**: 11 September 2024  
**Authors**: Mohamed Kanu, Sammy Oppong, Jaline Gerardin

---

## 📂 Table of Contents

<details>
<summary>Overview</summary>

## [Motivation](#motivation)
## [Objectives](#objectives)
## [Target audience](#target-audience)
## [Scope](#scope)

### Motivation
SNT is here to stay: many NMCPs have found it useful and are continuing to embrace it and further develop it for their analytical needs. Since 2019, multiple individuals have supported the analysis portions of SNT. In most cases, individuals have built their own code in a variety of languages (Stata, R, and Python), sometimes building on others’ previous code and sometimes re-developing independently.

As SNT matures, more quality assurance is needed so that NMCPs can be confident that the analysis used to inform their decisions is of high quality, regardless of the individual supporting the analyst. Continued rollout also means that analysis can become more efficient if analysts are better able to build on each other’s work, rather than tempted to reinvent what has already been developed. Lastly, SNT analysis can become much more accessible if there is a common resource available to help those with intermediate coding skills quickly access the collective knowledge of the SNT analyst community.


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

## Overview

### Motivation
SNT is here to stay: many NMCPs have found it useful and are continuing to embrace it and further develop it for their analytical needs. Since 2019, multiple individuals have supported the analysis portions of SNT. In most cases, individuals have built their own code in a variety of languages (Stata, R, and Python), sometimes building on others’ previous code and sometimes re-developing independently.

As SNT matures, more quality assurance is needed so that NMCPs can be confident that the analysis used to inform their decisions is of high quality, regardless of the individual supporting the analyst. Continued rollout also means that analysis can become more efficient if analysts are better able to build on each other’s work, rather than tempted to reinvent what has already been developed. Lastly, SNT analysis can become much more accessible if there is a common resource available to help those with intermediate coding skills quickly access the collective knowledge of the SNT analyst community.

### Objectives
We will build a code library for SNT analysis to:
- Ensure that SNT analysts are using similar, correct approaches
- Improve efficiency of SNT analysis by minimizing duplication of effort
- Promote accessibility of SNT analysis by lowering barriers to entry

### Target audience
Anyone doing this kind of work. We assume some basic knowledge of R, some understanding of the data, and a strong connection to the NMCP.


### Scope
All analysis steps of SNT up to but not including mathematical modeling; some related analysis.

The code library will be in R and publicly available. It will be quality-assured and well-commented.

When multiple algorithmic options could be used, strengths and limitations of each one, along with discussion of when to use each option, as possible.

Framing text, and when possible the code comments, will be available in both English and French.

---

## Library elements

### A. DATA ASSEMBLY AND MANAGEMENT
#### A.1 Shapefiles
- **A.1.1** Import shapefiles
- **A.1.2** Rename and match names
- **A.1.3** Link shapefiles to relevant scales
- **A.1.4** Visualizing shapefiles and making basic maps
#### How to do it
```r


     The code goes here with step by step explanation


```

#### A.2 Health Facilities
- **A.2.1** Get MFL from the Malaria Program
  - **A.2.1.1** Useful Columns:
    - adm0 - country
    - adm1 - province/ region
    - adm2 - district
    - adm3 - subdistrict/sub-county
    - Health Facility (HF)
    - Date HF started reporting
    - Is HF still active?
    - Type of HF (District hospital, health post, etc.)
