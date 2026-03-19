# INTERNAL MASTER PLAN: The AI-Accelerated Migration Challenge
**Classification:** CONFIDENTIAL / ORGANIZERS ONLY

---

## 1. The Mission (Participant Facing)
The objective is to modernize the data stack for *MediSynth*, a legacy healthcare provider. Participants must migrate archaic data into a modern **Medallion Architecture (Bronze -> Silver -> Gold)** using **AI-Driven Engineering** frameworks (BMAD).

---

## 2. The Legacy Sabotage (CONFIDENTIAL)
To evaluate the effectiveness of AI Acceleration, the source **Synthea** data must be intentionally "sabotaged" before handover. 

### Specific Sabotage Hurdles:
1.  **Cryptic Header Obfuscation:** Rename standard Synthea headers to mainframe codes (e.g., `PT_001_ID`, `GDR_CD`).
2.  **Date Format Chaos:** Mix date formats within the same column (ISO, DD/MM/YY, and Unix).
3.  **Nested & Inconsistent JSON:** Deliver `Observations` with raw JSON strings inside CSV columns.
4.  **Relationship Deletion:** Remove all Primary/Foreign key metadata. 
5.  **Enum Obfuscation:** Replace status with codes '1/0' or 'X/Z' (Key is in `/docs`).

---

## 3. The Rules of Engagement
* **AI-First Approach:** Participants must use **BMAD (AI Framework)** and LLMs.
* **Medallion Standard:** Final output must follow Bronze, Silver, and Gold layers.
* **The Prompt Journal:** Participants MUST maintain a log of all prompts used for evaluation.

---

## 4. Full Judging Criteria & Scorecard (CONFIDENTIAL)

| Category | Weight | Logic & Validation Method |
| :--- | :--- | :--- |
| **Data Fidelity** | **40%** | Automated SQL check against "Golden Record". |
| **AI/BMAD Mastery** | **30%** | Review of Prompt Journal depth and automation levels. |
| **Engineering** | **20%** | Review of DQ tests and AI-generated Lineage. |
| **Velocity** | **10%** | Lead time vs. manual effort estimates. |

### The "Golden Record" SQL Validation:
```sql
-- Internal query to calculate Match Rate
SELECT 
    (COUNT(p.patient_id) FILTER (WHERE p.gender = g.gender AND p.birth_date = g.birth_date) / COUNT(g.patient_id)) * 100 as fidelity_score
FROM participant_gold_table p
FULL OUTER JOIN hidden_golden_record g ON p.patient_id = g.patient_id;
```

---

## 5. Artifacts & Handover Logistics
* **Landing Zone:** S3/Blob storage containing the `/raw` sabotaged CSVs.
* **Context Folder (`/docs`):** A "Legacy Legend" for AI context (RAG).
* **Starter Kit:** Template to initialize BMAD and LLM endpoints.

---

## 6. Execution Roadmap
1.  **Preparation:** Sabotage Synthea data & Lock Golden Record.
2.  **Enablement:** Conduct "Prompt Engineering" pre-workshop.
3.  **The Sprint:** 48-hour development window.
4.  **The Judgment:** Run automated fidelity scripts.

---

## 7. Organizer Key Mapping Guide (PK/FK Candidates)

The raw files intentionally remove PK/FK metadata. Organizers should evaluate whether
candidates reconstruct these relationships in Silver.

### Canonical key candidates by table

- `patients`
  - Candidate PK: `PT_001_ID`
  - Referenced by: `encounters.PT_REF`, `conditions.PT_REF`, `medications.PT_REF`,
    `observations.PT_REF`

- `encounters`
  - Candidate PK: `ENC_KEY`
  - Candidate FK to patients: `PT_REF -> patients.PT_001_ID`
  - Referenced by: `conditions.ENC_REF`, `medications.ENC_REF`, `observations.ENC_REF`

- `conditions`
  - Candidate PK: `CND_KEY`
  - Candidate FK to patients: `PT_REF -> patients.PT_001_ID`
  - Candidate FK to encounters: `ENC_REF -> encounters.ENC_KEY`

- `medications`
  - Candidate PK: `MED_KEY`
  - Candidate FK to patients: `PT_REF -> patients.PT_001_ID`
  - Candidate FK to encounters: `ENC_REF -> encounters.ENC_KEY`

- `observations`
  - Candidate PK: `OBS_KEY`
  - Candidate FK to patients: `PT_REF -> patients.PT_001_ID`
  - Candidate FK to encounters: `ENC_REF -> encounters.ENC_KEY`

### Header alias note for organizer review

Some providers use renamed headers to increase ambiguity. Use each provider file:
`data/data_provider_*/columns_definition.md`
to map aliases to canonical headers before scoring relationship reconstruction.

### Data quality caveats for key validation

- `PT_001_ID` can be empty or duplicated by design.
- `PT_REF` and `ENC_REF` can be empty or contain unknown values (for sabotage).
- Scoring should reward deterministic key repair logic, not raw key completeness.