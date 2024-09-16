# CODE LIBRARY for SUB-NATIONAL TAILORING

**Version**: 13 September 2024  
**Authors**: Mohamed Kanu, Sammy Oppong, Jaline Gerardin

## Table of Contents
- [Overview](#overview)
- [Motivation](#motivation)
- [Objectives](#objectives)
- [Target audience](#target-audience)
- [Scope](#scope)
- [Library elements](#library-elements)
  - [A. DATA ASSEMBLY AND MANAGEMENT](#a-data-assembly-and-management)
    - [A.1 Shapefiles](#a1-shapefiles)
    - [A.2 Health Facilities](#a2-health-facilities)
    - [A.3 Routine case data from DHIS2](#a3-routine-case-data-from-dhis2)
    - [A.4 DHS data](#a4-dhs-data)
    - [A.5 Climate data](#a5-climate-data)
    - [A.6 LMIS data](#a6-lmis-data)
    - [A.7 Modeled data](#a7-modeled-data)
    - [A.8 Population data](#a8-population-data)
  - [B. EPIDEMIOLOGICAL STRATIFICATION](#b-epidemiological-stratification)
  - [C. STRATIFICATION OF OTHER DETERMINANTS](#c-stratification-of-other-determinants)
  - [D. REVIEW OF PAST INTERVENTIONS](#d-review-of-past-interventions)
  - [E. Targeting of interventions](#e-targeting-of-interventions)
  - [F. Retrospective analysis](#f-retrospective-analysis)
  - [G. Urban microstratification](#g-urban-microstratification)

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
  #### How to do it
```r

     The code goes here with step by step explanation


```
  
- **A.2.2** Get DHIS2 Health Facility (HF) List from the Malaria Program
  - **A.2.2.1** Useful Columns:
    - adm0, adm1, adm2, adm3
    - Health Facility (HF)
    - Date HF started reporting in DHIS2
    - Is HF still active?
    - Type of HF (MCHP, CHP, CHC, Hospital)
   
  #### How to do it
```r

     The code goes here with step by step explanation


```

- **A.2.3** Reconciling the MFL and the DHIS2 HF list
  - **A.2.3.1** Identifying common HFs in both lists using fuzzy name matching
  - **A.2.3.2** Reconciling inconsistent HF Type
  - **A.2.3.3** Reconciling HF adm1, adm2, adm3 designation
 
    #### How to do it
```r

     The code goes here with step by step explanation


```

- **A.2.4** HF active / inactive status
  - Determining activity status from MFL and DHIS2
 
    #### How to do it
```r

     The code goes here with step by step explanation


```

#### A.3 Routine case data from DHIS2
- **A.3.1** Data extraction and import process
- **A.3.2** Sanity Checks (column names, dataset length)
- **A.3.3** Merging datasets, handling duplicates
- **A.3.4** Data cleaning (exploration, renaming variables, handling missing data)
- **A.3.5** Outlier detection and correction

#### How to do it
```r

     The code goes here with step by step explanation


```
#### A.4 DHS data
#### A.5 Climate data
#### A.6 LMIS data
#### A.7 Modeled data
#### A.8 Population data

#### How to do it
```r

     The code goes here with step by step explanation


```

---

### B. EPIDEMIOLOGICAL STRATIFICATION
- **B.1** Reporting Rate per Variable
- **B.2** Group and merge data frame
- **B.3** Crude Incidence by Year
- **B.4** Adjusted Incidence by Year
- **B.5** Option to Select Incidence
- **B.6** Risk Categorization

- #### How to do it
```r

     The code goes here with step by step explanation


```

---

### C. STRATIFICATION OF OTHER DETERMINANTS
- **C.1** Access to Care
- **C.2** Seasonality
- **C.3** Insecticide Resistance
- **C.4** Anti-Malaria Drug Resistance

#### How to do it
```r

     The code goes here with step by step explanation


```

---

### D. REVIEW OF PAST INTERVENTIONS
- **D.1** EPI Coverage and Dropout Rate
- **D.2** IPTp and ANC Coverage
- **D.3** PMC (Prevention of Malaria in Pregnancy)
- **D.4** SMC (Seasonal Malaria Chemoprevention)
- **D.5** Malaria Vaccine
- **D.6** ITN Ownership, Access, Usage, and Type
- **D.7** ITN Operational Coverage
- **D.8** IRS (Indoor Residual Spraying)
- **D.9** LSM (Larval Source Management)
- **D.10** Assessing the Quality of Case Management

  #### How to do it
```r

     The code goes here with step by step explanation


```

---

### E. Targeting of interventions
### F. Retrospective analysis
### G. Urban microstratification

#### How to do it
```r

     The code goes here with step by step explanation


```

### NB

---

## NB
Draft version as of 13th September 2024.
