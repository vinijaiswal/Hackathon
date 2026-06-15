# External Datasets for CarePath India (data.gov.in)

Source: data.gov.in Open Government Data Platform India
Purpose: Augment Virtue Foundation dataset for CarePath India on Databricks Genie
License: Government Open Data License India GODL

---

## 1. FACILITY DATASETS

### 1.1 National Hospital Directory Geocoded - HIGH PRIORITY
URL: https://data.gov.in/resource/national-hospital-directory-geo-code-and-additional-parameters-updated-till-last-month
Update: Monthly. Contains: All registered hospitals with lat/lon, district, state, bed count, ownership type.
Use for: Fix facility-matching in Genie, geocode Virtue Foundation records, compute distances.

### 1.2 PHC Primary Health Centers - HIGH PRIORITY
URL: https://data.gov.in/resource/primary-health-center

### 1.3 CHC Community Health Centers - HIGH PRIORITY
URL: https://data.gov.in/resource/community-health-center

### 1.4 Tertiary Health Centers THC - HIGH PRIORITY
URL: https://data.gov.in/resource/tertiary-health-center

### 1.5 Health and Wellness Centers - HIGH PRIORITY
URL: https://data.gov.in/resource/health-wellness-center

### 1.6 Sub-Centers - HIGH PRIORITY
URL: https://data.gov.in/resource/sub-center

### 1.7 Blood Storage Centers - HIGH PRIORITY
URL: https://data.gov.in/resource/blood-storage-center
Use for: Blood transfusion matching for chemo patients.

### 1.8 District Hospitals Karnataka - MEDIUM PRIORITY
URL: https://data.gov.in/resource/district-hospital

### 1.9 Taluk Hospitals Karnataka - MEDIUM PRIORITY
URL: https://data.gov.in/resource/taluk-hospital

### 1.10 AYUSH Facilities - MEDIUM PRIORITY
Ayurveda: https://data.gov.in/resource/govt-ayurveda-hospital
Homoeopathy: https://data.gov.in/resource/govt-homoeopathy-hospital

---

## 2. PATIENT POPULATION AND EPIDEMIOLOGY

### 2.1 ICMR-NCRP Cancer Incidence - HIGH PRIORITY
URL: https://data.gov.in/resource/year-wise-number-cancer-cases-breast-cancer-indian-council-medical-research-national
Use for: Benchmark cohort vs expected prevalence, calibrate district models.

### 2.2 NFHS-5 District Factsheets 2019-2021 - HIGH PRIORITY
State: https://data.gov.in/resource/all-india-and-stateut-wise-factsheets-national-family-health-survey-nfhs-5-2019-2021
District: https://data.gov.in/resource/india-districts-factsheets-national-family-health-survey-nfhs-5-2019-2021-provisional
Contains: 300+ indicators per district - anaemia, tobacco use, insurance coverage, nutrition.
Use for: Impute missing SES fields in Virtue Foundation, risk-stratify patients by district.

### 2.3 Cancer Control Programme Patients Treated - MEDIUM PRIORITY
URL: https://data.gov.in/resource/patients-treated-cancer-under-cancer-control-programme-2014-15

---

## 3. GEOGRAPHIC REFERENCE

### 3.1 All India Pincode Directory - HIGH PRIORITY
URL: https://data.gov.in/resource/all-india-pincode-directory-till-last-month
Update: Monthly, 155000+ pincodes with lat/lon.
Use for: Fix missing/inconsistent addresses in Virtue Foundation, derive district from pincode, compute distances.

### 3.2 LGD Villages with PIN Codes - MEDIUM PRIORITY
URL: https://data.gov.in/resource/local-government-directory-lgd-villages-pin-codes
Use for: Deduplicate location names (Bangalore vs Bengaluru), common geo-key for Databricks joins.

---

## 4. TREATMENT AND FINANCIAL

### 4.1 Oncology Drug Rates AMRIT AIIMS - MEDIUM PRIORITY
URL: https://data.gov.in/resource/finalised-rates-oncology-drugs-amrit-pharmacy-aiims-new-delhi-07122015-ministry-health-and

### 4.2 PG Oncology Training Courses - MEDIUM PRIORITY
URL: https://data.gov.in/resource/course-wise-post-graduate-training-oncology-provided-broad-specialty-and-super-specialty

### 4.3 HMCPF Cancer Patient Fund - MEDIUM PRIORITY
URL: https://data.gov.in/resource/year-wise-number-beneficiaries-under-health-ministers-cancer-patient-fund-hmcpf-2019-20

---

## 5. DATABRICKS SCHEMA RECOMMENDATION

dim_facilities: facility_id, facility_name, facility_type, ownership, district, state, pincode, latitude, longitude, bed_count, has_oncology, source
dim_geography: pincode, district, state, latitude, longitude, nfhs5_anaemia_prev, nfhs5_tobacco_use, nfhs5_health_insurance_pct, nfhs5_facility_birth_pct

Join to Virtue Foundation fact_patients on pincode or district.

---
Last updated: June 2026 | DAIS Hackathon Table 34 - CarePath India
