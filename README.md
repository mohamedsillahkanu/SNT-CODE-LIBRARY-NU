# CODE LIBRARY for SUB-NATIONAL TAILORING

**Version**: 11 September 2024  
**Authors**: Mohamed Kanu, Sammy Oppong, Jaline Gerardin  

---

## Table of Contents

- [Overview](#overview)
- [Motivation](#motivation)
- [Objectives](#objectives)
- [Target Audience](#target-audience)
- [Scope](#scope)
- [Library Elements](#library-elements)
  - [A DATA ASSEMBLY AND MANAGEMENT](#a-data-assembly-and-management)
    - [A.1 Shapefiles](#a1-shapefiles)
    - [A.2 Health Facilities](#a2-health-facilities)
    - [A.3 Routine case data from DHIS2](#a3-routine-case-data-from-dhis2)
    - [A.4 DHS data](#a4-dhs-data)
    - [A.5 Climate data](#a5-climate-data)
    - [A.6 LMIS data](#a6-lmis-data)
    - [A.7 Modeled data](#a7-modeled-data)
    - [A.8 Population data](#a8-population-data)
  - [B EPIDEMIOLOGICAL STRATIFICATION](#b-epidemiological-stratification)
    - [B.1 Reporting Rate per Variable](#b1-reporting-rate-per-variable)
    - [B.2 Group and merge data frame](#b2-group-and-merge-data-frame)
    - [B.3 Crude Incidence by Year](#b3-crude-incidence-by-year)
    - [B.4 Adjusted Incidence by Year](#b4-adjusted-incidence-by-year)
    - [B.5 Option to Select Incidence](#b5-option-to-select-incidence)
    - [B.6 Risk Categorization](#b6-risk-categorization)
  - [C STRATIFICATION OF OTHER DETERMINANTS](#c-stratification-of-other-determinants)
    - [C.1 Access to Care](#c1-access-to-care)
    - [C.2 Seasonality](#c2-seasonality)
    - [C.3 Insecticide Resistance](#c3-insecticide-resistance)
    - [C.4 Anti-Malaria Drug Resistance](#c4-anti-malaria-drug-resistance)
  - [D REVIEW OF PAST INTERVENTIONS](#d-review-of-past-interventions)
    - [D.1 EPI Coverage and Dropout Rate](#d1-epi-coverage-and-dropout-rate)
    - [D.2 IPTp and ANC Coverage](#d2-iptp-and-anc-coverage)
    - [D.3 PMC (Prevention of Malaria in Pregnancy)](#d3-pmc-prevention-of-malaria-in-pregnancy)
    - [D.4 SMC (Seasonal Malaria Chemoprevention)](#d4-smc-seasonal-malaria-chemoprevention)
    - [D.5 Malaria Vaccine](#d5-malaria-vaccine)
    - [D.6 ITN Ownership, Access, Usage, and Type](#d6-itn-ownership-access-usage-and-type)
    - [D.7 ITN Operational Coverage](#d7-itn-operational-coverage)
    - [D.8 IRS (Indoor Residual Spraying)](#d8-irs-indoor-residual-spraying)
    - [D.9 LSM (Larval Source Management)](#d9-lsm-larval-source-management)
    - [D.10 Assessing the Quality of Case Management](#d10-assessing-the-quality-of-case-management)
  - [E Targeting of interventions](#e-targeting-of-interventions)
  - [F Retrospective analysis](#f-retrospective-analysis)
  - [G Urban microstratification](#g-urban-microstratification)

---

## Overview

## Motivation
SNT is here to stay: many NMCPs have found it useful and are continuing to embrace it and further develop it for their analytical needs. Since 2019, multiple individuals have supported the analysis portions of SNT. In most cases, individuals have built their own code in a variety of languages (Stata, R, and Python), sometimes building on others’ previous code and sometimes re-developed independently.

As SNT matures, more quality assurance is needed such that NMCPs can be confident that the analysis they use to inform their decisions is of high quality regardless of the individual supporting analyst. The continued rollout of SNT also means that analysis can become more efficient if analysts are better able to build on each other’s work rather than tempted to reinvent what has already been developed. Lastly, SNT analysis can become much more accessible if there is a common resource available to help those with intermediate coding skills quickly access the collective knowledge of the SNT analyst community.

## Objectives
We will build a code library for SNT analysis to:

- Ensure that SNT analysts are using similar, correct approaches
- Improve efficiency of SNT analysis by minimizing duplication of effort
- Promote accessibility of SNT analysis by lowering barriers to entry

## Target Audience
Anyone doing this kind of work. We assume some basic knowledge of R, some understanding of the data, and a strong connection to the NMCP.

## Scope
All analysis steps of SNT up to but not including mathematical modeling; some related analysis.

The code library will be in R and publicly available. It will be quality-assured and well-commented.

When multiple algorithmic options could be used, strengths and limitations of each one, along with discussion of when to use each option, as possible.

Framing text, and when possible the code comments, will be available in both English and French.

---

## Library Elements

### A DATA ASSEMBLY AND MANAGEMENT

#### A.1 Shapefiles
- **A.1.1** Import shapefiles
- **A.1.2** Rename and match names
- **A.1.3** Link shapefiles to relevant scales
- **A.1.4** Visualizing shapefiles and making basic maps

#### A.2 Health Facilities
- **A.2.1** Get MFL from the Malaria Program
  - **Useful Columns**:
    - adm0 - country
    - adm1 - province/region
    - adm2 - district
    - adm3 - sub-district/sub-county
    - Health Facility (HF)
    - Date HF started reporting
    - Is HF still active?
    - If no, when did HF become inactive?
    - Type of HF (District hospital, teaching hospital, health post, etc.)
- **A.2.2** Get the DHIS2 Health Facility (HF) List from the Malaria Program
  - **Useful Columns**:
    - adm0
    - adm1
    - adm2
    - adm3
    - Health Facility (HF)
    - Date HF started reporting in DHIS2
    - Is HF still active? 
    - If no, when did HF become inactive? 
    - Type of HF (MCHP, CHP, CHC, Hospital)
- **A.2.3** Reconciling the MFL and the DHIS2 HF list
  - **Identifying HFs in both or one list based on HF name**
    - Identifying common HFs (accounting for differences in Spellings, Typos, Spaces, Capitalization) in 2 databases: algorithms for fuzzy name matching
    - **Output**: 
      - HF in both DHIS2 and MFL
      - HF in MFL but not in DHIS2
      - HF in DHIS2 but not in MFL
  - **Reconciling inconsistent HF Type (MCHP, CHP, CHC, Hospital)**
    - Check HF type in both databases
    - Resolve any inconsistencies
  - **Reconciling HF adm1, adm2, and adm3 designation**
    - Check HF adm 1/2/3 designation in both databases
    - Resolve any inconsistencies
- **A.2.4** HF active/inactive status
  - **Determining active/inactive status from MFL**
  - **Determining active/inactive status from DHIS2**
  - **Determining when HF ceased reporting entirely**
  - **Reconciling differences in activity status from MFL and DHIS2**
  - **Health Facility Reporting Periods**
    - Active Reporting Periods
    - Inactive Reporting Periods            
  - **Health Facility Reporting Frequency**
    - Continuously Reporting Health Facilities
    - Intermittently Reporting Health Facilities (with Gaps)
    - Health Facilities that Reported Only Once
    - First-Time Reporting Health Facilities
    - Last-Time Reporting Health Facilities
  - **Output**: One HF database (with active and inactive HFs) & Visualization (Heatmap)
- **A.2.5** Restricting HFs in database
  - **Removing HFs before they become active**
  - **Removing HFs after they are permanently inactive**
  - **…what are other options? Continue on this list**
  - **Output**: Cleaned HF database
- **A.2.6** Summary outputs
  - **Summary data file**: HF Expected to Report by adm1/adm2/adm3 Per Year, Per Month
  - **Visualizing with graphs, heatmaps, or maps** (yearly/monthly reporting rates by adm1/adm2/adm3)

#### A.3 Routine case data from DHIS2
- **A.3.1** Import and clean routine case data from DHIS2
- **A.3.2** Data summarization and aggregation 
- **A.3.3** Data transformation and preparation for analysis

#### A.4 DHS data
- **A.4.1** Import and clean DHS data
- **A.4.2** Data summarization and analysis
- **A.4.3** Linking DHS data to HF data

#### A.5 Climate data
- **A.5.1** Import and clean climate data
- **A.5.2** Data summarization and integration with health data
- **A.5.3** Visualization of climate data effects on health outcomes

#### A.6 LMIS data
- **A.6.1** Import and clean LMIS data
- **A.6.2** Data summarization and integration
- **A.6.3** Visualization of LMIS data effects on health outcomes

#### A.7 Modeled data
- **A.7.1** Import and clean modeled data
- **A.7.2** Data summarization and analysis
- **A.7.3** Linking modeled data to health data

#### A.8 Population data
- **A.8.1** Import and clean population data
- **A.8.2** Data summarization and analysis
- **A.8.3** Linking population data to health outcomes

---

### B EPIDEMIOLOGICAL STRATIFICATION

#### B.1 Reporting Rate per Variable
- **B.1.1** Calculate reporting rates
- **B.1.2** Visualization of reporting rates

#### B.2 Group and merge data frame
- **B.2.1** Grouping data by relevant categories
- **B.2.2** Merging datasets for comprehensive analysis

#### B.3 Crude Incidence by Year
- **B.3.1** Calculate crude incidence rates
- **B.3.2** Visualization of crude incidence

#### B.4 Adjusted Incidence by Year
- **B.4.1** Calculate adjusted incidence rates
- **B.4.2** Visualization of adjusted incidence

#### B.5 Option to Select Incidence
- **B.5.1** Implement options for users to select incidence types
- **B.5.2** Visual representation based on selected incidence

#### B.6 Risk Categorization
- **B.6.1** Classifying risks based on criteria
- **B.6.2** Visualization of risk categories

---

### C STRATIFICATION OF OTHER DETERMINANTS

#### C.1 Access to Care
- **C.1.1** Assessing access to healthcare services
- **C.1.2** Visualization of access disparities

#### C.2 Seasonality
- **C.2.1** Analyzing seasonal trends in health data
- **C.2.2** Visualization of seasonal patterns

#### C.3 Insecticide Resistance
- **C.3.1** Assessing insecticide resistance data
- **C.3.2** Visualization of resistance trends

#### C.4 Anti-Malaria Drug Resistance
- **C.4.1** Analyzing drug resistance data
- **C.4.2** Visualization of resistance trends

---

### D REVIEW OF PAST INTERVENTIONS

#### D.1 EPI Coverage and Dropout Rate
- **D.1.1** Assessing EPI coverage rates
- **D.1.2** Visualization of dropout rates

#### D.2 IPTp and ANC Coverage
- **D.2.1** Analyzing IPTp and ANC coverage
- **D.2.2** Visualization of coverage rates

#### D.3 PMC (Prevention of Malaria in Pregnancy)
- **D.3.1** Assessing PMC coverage and effectiveness
- **D.3.2** Visualization of PMC data

#### D.4 SMC (Seasonal Malaria Chemoprevention)
- **D.4.1** Assessing SMC coverage and effectiveness
- **D.4.2** Visualization of SMC data

#### D.5 Malaria Vaccine
- **D.5.1** Analyzing malaria vaccine coverage and efficacy
- **D.5.2** Visualization of vaccine data

#### D.6 ITN Ownership, Access, Usage, and Type
- **D.6.1** Assessing ITN ownership and access
- **D.6.2** Visualization of ITN data

#### D.7 ITN Operational Coverage
- **D.7.1** Analyzing ITN operational coverage
- **D.7.2** Visualization of coverage data

#### D.8 IRS (Indoor Residual Spraying)
- **D.8.1** Assessing IRS coverage and impact
- **D.8.2** Visualization of IRS data

#### D.9 LSM (Larval Source Management)
- **D.9.1** Analyzing LSM coverage and effectiveness
- **D.9.2** Visualization of LSM data

#### D.10 Assessing the Quality of Case Management
- **D.10.1** Evaluating the quality of case management
- **D.10.2** Visualization of quality assessment

---

### E Targeting of interventions
- **E.1** Criteria for targeting interventions
- **E.2** Visualization of targeted intervention areas

---

### F Retrospective analysis
- **F.1** Analyzing historical health data
- **F.2** Lessons learned from past interventions

---

### G Urban microstratification
- **G.1** Analyzing urban health dynamics
- **G.2** Visualization of urban stratification data
