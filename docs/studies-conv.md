---
id: studies-conv
title: CONVALESCENT SERUM (CS) STUDY
hide_title: true
---
<h1>Convalescent <span>Serum</span></h1>

**RESEARCH QUESTION: For patients with new COVID-19 infection, how does the addition of convalescent serum (CS) affect the outcomes (1) severe disease (indicated by mechanical ventilation) and (2) inpatient death?**

> Notice:
This content is rough draft or placeholder quality, and is expected to change quickly as we work with C19HCC partners to align and refine definitions.


### Background

CS is currently under study as possible treatments for COVID-19. Before randomized clinical trials read out, a retrospective observational study can provide insight into the efficacy of this treatment.

### Study Design

The study examines the effect of CS treatment in hospitalized COVID-19 patients on disease severity. The study involves two study groups (those receiving or not receiving CS), as depicted below:

**Study Period**: January 1, 2020 - Present (Index date: `COVID-19-positive-date`)

![Convalescent Serum cohort pathways](cs_cohorts.png)

Three outcomes are considered:

1. Discharge without invasive mechanical ventilation (IMV) during stay
2. Discharge after IMV during stay
3. Inpatient death

These outcomes correspond to increasing levels disease severity. The study uses mechanical ventilation as a proxy for severe but non-fatal disease. The outcome is retrospective over the entire patient visit and capture the worst severity of illness during the visit. For example:

* Patient is put on a ventilator (level 2) and then succumbs to the disease (level 3); the outcome is level 3 (death).
* Patient is temporarily put on a ventilator (level 2), then taken off the ventilator (level 1) and discharged; the outcome level 2.

Alternatively, results can be reported in terms of four outcomes:

1. Discharge without IMV during stay
2. Discharge with IMV during stay
3. Inpatient death:<br/>
  a. Death without IMV during stay<br/>
  b. Death with IMV during stay

Data with four outcome categories can be easily transformed into three categories, since categories 3a and 3b together account for all patient deaths, category 3.

### Study Populations

* **Entry Cohort**:
  * Age at `COVID-19-positive-date` ≥ 18 years AND
  * `COVID-19-positive-date` after Jan 1, 2020 AND
  * `COVID-19-related hospitalization`
* **Target Cohort**:
  * Entry Cohort AND `Inpatient-CS-use`
* **Control Cohort**:
  * Entry Cohort AND NOT `Inpatient-CS-use`

### Definitions

* `COVID-19-positive` [2]:
  * Any clinical diagnosis [3] code in set `C19HCC Confirmed COVID-19 infection` OR
  * `Positive` or `detected` result from any test in set `C19HCC SARS-CoV-2 Qualitative Laboratory Test` [4] OR
  * `Positive` or `detected` result from any test in set `C19HCC SARS-related Qualitative Laboratory Test` [4]
* `COVID-19-positive-date`: earliest date of `COVID-19-positive` [5]
* `Hospitalization`:
  * encounter with class or type like `inpatient encounter` AND
  * encounter status like `completed`
* `COVID-19-related-hospitalization`: [6]
  * `COVID-19-positive-date` during `hospitalization` OR
  * (`hospitalization` up to 14 days after `COVID-19-positive-date`) AND (any clinical or billing diagnosis of `Respiratory Condition` associated with the hospitalization [7])
* `Inpatient-CS-use`:
  * Any administration of CS during `COVID-19-related-hospitalization`
    * Includes any dose or duration of CS
    * Includes any level of disease severity while on CS
    * Includes patients on other medications

### Outcomes

* **Invasive Mechanical Ventilation (IMV)**:
  * `Invasive mechanical ventilation` procedure during `COVID-19-related-hospitalization` OR
  * Evidence mechanical ventilation in ICU flowsheet documentation (e.g. ventilator mode change)[8]

* **COVID-19 Inpatient Death**:
  * `COVID-19 related hospitalization` discharge disposition like `expired` OR date of death is during `COVID-19 related hospitalization`

### Value Sets

* [C19HCC Confirmed COVID-19 Infection](https://vsac.nlm.nih.gov/valueset/2.16.840.1.113762.1.4.1032.117/expansion/Latest) (SNOMED CT, ICD-10-CM)
* [C19HCC SARS-CoV-2 Qualitative Laboratory Test](https://vsac.nlm.nih.gov/valueset/2.16.840.1.113762.1.4.1032.109/expansion/Latest) (LOINC)
* [C19HCC SARS-related Qualitative Laboratory Test](https://vsac.nlm.nih.gov/valueset/2.16.840.1.113762.1.4.1032.113/expansion/Latest) (LOINC)
* [Convalescent Serum]() -- TBD
* Invasive mechanical ventilation: Any intubation procedure or mechanical ventilation-associated procedure. Excludes supplemental oxygen (high or low flow), CPAP, and BiPAP, ECMO (SNOMED CT, CPT, ICD-10-PCS)

#### Notes:

[2] Study includes confirmed cases only<br/>
[3] A clinical diagnosis can be any diagnosis associated with an encounter, such as chief complaint, admitting diagnosis, working diagnosis, final diagnosis, or discharge diagnosis. It can also be a problem list entry.<br/>
[4] There may be local value sets/groupers for laboratory tests to detect SARS-CoV-2. Only PCR and NAAT tests with qualitative results should be considered for this purpose. See [C19HCC SARS-CoV-2 Qualitative Laboratory Test](https://vsac.nlm.nih.gov/valueset/2.16.840.1.113762.1.4.1032.109/expansion/Latest) and [C19HCC SARS-related Qualitative Laboratory Test]() for details on inclusions and exclusions.<br/>
[5] The relevant date for laboratory test is the specimen collection data, not when results are reported. Laboratory order date can be used when specimen collection date is not available.<br/>
[6] This definition includes patients diagnosed with COVID-19 during a hospital visit even if the reason for hospitalization is not COVID-related; e.g., patients with undetected COVID-19 admitted for other reasons, and nosocomial COVID-19 infections ​<br/>
[7] Serves a confirmation that hospital admission is related to COVID-19 infection (as opposed to broken arm, etc.)<br/>
[8] ICU flowsheet data may not be accessible to all data partners