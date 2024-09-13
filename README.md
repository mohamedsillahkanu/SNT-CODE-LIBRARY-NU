# CODE LIBRARY for SUB-NATIONAL TAILORING

**Version**: 13 September 2024  
**Authors**: Mohamed Kanu, Sammy Oppong, Jaline Gerardin

---

## Table of Contents (Sidebar)

- [Overview](#overview)
- [Motivation](#motivation)
- [Objectives](#objectives)
- [Target Audience](#target-audience)
- [Scope](#scope)
- [Library Elements](#library-elements)
  - [A. DATA ASSEMBLY AND MANAGEMENT](#a-data-assembly-and-management)
    - [A.1 Shapefiles](#a1-shapefiles)
    - [A.2 Health Facilities](#a2-health-facilities)
    - [A.3 Routine Case Data from DHIS2](#a3-routine-case-data-from-dhis2)
    - [A.4 DHS Data](#a4-dhs-data)
    - [A.5 Climate Data](#a5-climate-data)
    - [A.6 LMIS Data](#a6-lmis-data)
    - [A.7 Modeled Data](#a7-modeled-data)
    - [A.8 Population Data](#a8-population-data)
  - [B. EPIDEMIOLOGICAL STRATIFICATION](#b-epidemiological-stratification)
  - [C. STRATIFICATION OF OTHER DETERMINANTS](#c-stratification-of-other-determinants)
  - [D. REVIEW OF PAST INTERVENTIONS](#d-review-of-past-interventions)
  - [E. TARGETING OF INTERVENTIONS](#e-targeting-of-interventions)
  - [F. RETROSPECTIVE ANALYSIS](#f-retrospective-analysis)
  - [G. URBAN MICROSTRATIFICATION](#g-urban-microstratification)

---

## Overview

Welcome to the Code Library for Sub-National Tailoring. This document provides an overview of the library and its contents.

## Motivation

SNT is here to stay: many NMCPs have found it useful...

## Objectives

We aim to build a code library for SNT analysis to ensure...

## Target Audience

This library is intended for anyone doing this kind of work...

## Scope

The code library will cover all analysis steps...

---

## Library Elements

### A. DATA ASSEMBLY AND MANAGEMENT

#### A.1 Shapefiles

**A.1.1 Import shapefiles**
- Explanation on how to import shapefiles.

**A.1.2 Rename and match names**
- Steps to rename and match names.

**A.1.3 Link shapefiles to relevant scales**
- Details on linking shapefiles.

**A.1.4 Visualizing shapefiles and making basic maps**
- How to visualize shapefiles.

#### A.2 Health Facilities

**A.2.1 Get MFL from the Malaria Program**
- **Useful Columns**:
  - adm0 - country
  - adm1 - province/region
  - adm2 - district

**A.2.2 Get DHIS2 Health Facility (HF) List from the Malaria Program**
- **Useful Columns**:
  - adm0, adm1, adm2, adm3

**A.2.3 Reconciling the MFL and DHIS2 HF list**
- Steps for reconciliation.

**A.2.4 HF active/inactive status**
- Determining activity status.

#### A.3 Routine Case Data from DHIS2

**A.3.1 Data extraction and import process**
- Extraction and import steps.

**A.3.2 Sanity Checks**
- Checks for column names and dataset length.

**A.3.3 Merging datasets**
- Merging steps.

**A.3.4 Data cleaning**
- Cleaning steps and methods.

**A.3.5 Outlier detection and correction**
- Methods for detecting and correcting outliers.

[Continue with other sections…]

---

## NB
Draft version as of 13th September 2024.
